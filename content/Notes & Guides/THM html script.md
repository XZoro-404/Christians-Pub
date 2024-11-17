```python
import argparse
from bs4 import BeautifulSoup


def parse_html(html):
    soup = BeautifulSoup(html, 'html.parser')
    tasks = soup.find_all('div', class_='card')

    output = ""
    for task in tasks:
        task_header = task.find('div', class_='task-header')
        # task_number = task_header.find('span', class_='task-dropdown-title').text.strip()
        task_title_element = task_header.find('span', class_='task-dropdown-title')
        task_name = task_title_element.next_sibling.strip()

        task_desc = task.find('div', class_='room-task-desc').text.strip()

        # Exclude "start machine" from task description
        task_desc = task_desc.replace('Start Machine', '')

        output += f"## {task_name}\n---\n### Information\n{task_desc}\n"

        # Check for tables
        tables = task.find_all('table')
        for table in tables:
            output += str(table) + '\n\n'

        output += "### Questions\n"

        task_questions = task.find_all('div', class_='room-task-questions')
        for question in task_questions:
            question_text = question.find('div', class_='room-task-question-details').text.strip()
            output += f"\n*{question_text}*\n\n"
            # Extracting hint if available
            hint_button = question.find('button', class_='task-hint')
            if hint_button:
                hint_text = hint_button.find_next_sibling('div').text.strip()
                output += f"Hint: {hint_text}\n\n"
            output += ">[!question]- **Answer**\n>\n"

        # Check for images and include them with the same style and location
        # images = task.find_all('img')
        # for image in images:
        #     src = image['src']
        #     style = image['style']
        #     output += f'<img src="{src}" style="{style}">\n\n'

    return output


def write_output_file(output, filename):
    with open(filename, 'w') as f:
        f.write(output)

def main():
    parser = argparse.ArgumentParser(description="Parse HTML and generate output file.")
    parser.add_argument('-f', '--file', help="HTML file to parse.")
    args = parser.parse_args()

    if args.file:
        with open(args.file, 'r') as f:
            html = f.read()
    else:
        print("Please provide an HTML file.")
        exit()

    output = parse_html(html)
    output_file = args.file.split('.')[0] + ".md"
    write_output_file(output, output_file)
    print(f"Output file '{output_file}' generated successfully.")

if __name__ == "__main__":
    main()

```
