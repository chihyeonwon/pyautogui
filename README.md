# pyautogui
엑셀 자동화 업무 프로그램 개발 with Python
업무자동화프로그램 개발 증적 자료 제출용

개발기간 : 25년 3월 5일 ~

## Demo Python Code
1. 자동 공백 제거 프로그램  
```python
import pandas as pd

# 엑셀 파일 불러오기
file_path = "파일경로.xlsx"  # 실제 파일 경로로 변경
df = pd.read_excel(file_path, dtype=str)  # 문자열로 불러오기

# 모든 셀의 앞뒤 공백 제거
df = df.applymap(lambda x: x.strip() if isinstance(x, str) else x)

# 수정된 데이터 저장 (원본 덮어쓰기 또는 새 파일로 저장)
df.to_excel("수정된_파일.xlsx", index=False)  # 기존 파일명을 변경할 수도 있음

print("셀의 앞뒤 공백이 제거된 엑셀 파일이 저장되었습니다.")
```
