# webApp
## 프로젝트를 시작    
1. 새 폴더 만들고
2. 터미널에서 가상환경 만들기
```
conda create -n webApp python=3.9
```
3. 가상환경과 vscode 연결
![image](https://github.com/user-attachments/assets/8479262c-56b4-45b8-8e71-369caae1f84d)
4. Flask 프레임워크 설치
```
pip install flask
```
5. app.py 새 파일 만들기
6. flask 구조 완성하기 (feat coPilot 또는 chatGPT)
![image](https://github.com/user-attachments/assets/ecf7c4da-6494-4f50-a1e6-6af0dfc3beca)

7. 코드 생성
  1) app.py - 아래는 Flask를 이용해 이름과 전화번호를 입력받아 addbook.txt 파일에 CSV 형식으로 저장하는 간단한 웹 애플리케이션 코드입니다. HTML 템플릿도 함께 포함되어 있습니다.   

```
from flask import Flask, render_template, request, redirect
import csv

app = Flask(__name__)

# Route for the home page
@app.route('/')
def index():
    return render_template('index.html')

# Route to handle form submission
@app.route('/add', methods=['POST'])
def add_contact():
    name = request.form['name']
    phone = request.form['phone']

    # Save to addbook.txt in CSV format
    with open('addbook.txt', 'a', newline='', encoding='utf-8') as file:
        writer = csv.writer(file)
        writer.writerow([name, phone])

    return redirect('/')

if __name__ == '__main__':
    app.run(debug=True)
```
   2) templates/index.html 파일
Flask는 기본적으로 templates 폴더에서 HTML 파일을 찾습니다. 아래는 index.html 파일의 내용입니다.
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Address Book</title>
</head>
<body>
    <h1>Address Book</h1>
    <form action="/add" method="post">
        <label for="name">Name:</label>
        <input type="text" id="name" name="name" required>
        <br><br>
        <label for="phone">Phone:</label>
        <input type="text" id="phone" name="phone" required>
        <br><br>
        <button type="submit">Add Contact</button>
    </form>
</body>
</html>
```
   3) addbook.txt 파일
이 파일은 코드 실행 중에 자동으로 생성됩니다. 초기에는 빈 파일로 시작합니다.
## 프로그램 실행 방법 
```
python app.py
```
브라우저에서 http://127.0.0.1:5000로 접속하여 이름과 전화번호를 입력하고 저장할 수 있습니다.    
이제 Flask 애플리케이션이 완성되었습니다!    

## 실행 화면
![image](https://github.com/user-attachments/assets/18140a07-c51d-492b-88c0-797a7460a907)

## style 적용 화면 
<img width="612" alt="image" src="https://github.com/user-attachments/assets/2ab7df3b-9387-426c-b786-dd5d30784af2" />





 
