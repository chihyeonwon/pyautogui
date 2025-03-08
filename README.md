# pyautogui
엑셀 자동화 업무 프로그램 개발 with Python
업무자동화프로그램 개발 증적 자료 제출용

개발기간 : 25년 3월 5일 ~

## Demo Python Code
1. 자동 공백 제거 프로그램  
```python
import pandas as pd // pandas 라이브러리를 설치해주고~
import tkinter as tk // tkinter 라이브러리 gui 때문에 설치해주고~
from tkinter import filedialog, messagebox

def process_excel():
    # 파일 선택 일단은 경로명으로 파일 불러오게함~
    file_path = filedialog.askopenfilename(filetypes=[("Excel Files", "*.xlsx;*.xls")])
    
    if not file_path:
        return  # 사용자가 파일 선택을 취소하면 종료하도록 하고
    
    try:
        # 엑셀 파일 읽기 (문자열 데이터 유지)
        df = pd.read_excel(file_path, dtype=str)
        
        # 모든 셀의 앞뒤 공백 제거 기능 추가하고
        df = df.applymap(lambda x: x.strip() if isinstance(x, str) else x)
        
        # 새로운 파일명 설정 (기존 파일명 + "_수정본.xlsx") <- 요거는 어제날짜 자동으로 들어가게끔하고
        new_file_path = file_path.replace(".xlsx", "_수정본.xlsx").replace(".xls", "_수정본.xls")
        
        # 수정된 데이터 저장하고
        df.to_excel(new_file_path, index=False)

        # 완료 메시지 출력 <- 요거는 필요없을수도
        messagebox.showinfo("완료", f"수정된 파일이 저장되었습니다:\n{new_file_path}")
    
    except Exception as e:
        messagebox.showerror("오류", f"파일 처리 중 오류 발생:\n{str(e)}")

# GUI 생성
root = tk.Tk()
root.title("엑셀 공백 제거 프로그램")
root.geometry("300x150")

label = tk.Label(root, text="엑셀 파일을 선택하세요", font=("Arial", 12))
label.pack(pady=10)

btn = tk.Button(root, text="파일 선택 및 실행", command=process_excel, font=("Arial", 12))
btn.pack(pady=20)

root.mainloop()
```
