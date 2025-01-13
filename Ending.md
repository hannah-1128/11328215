import datetime

# 儲存行程的字典
calendar = {}

def show_schedule(date):
    """顯示指定日期的行程"""
    if date in calendar:
        print(f"\n{date} 的行程:")
        for idx, event in enumerate(calendar[date], start=1):
            print(f"  {idx}. {event}")
    else:
        print(f"\n{date} 沒有安排行程。")

def add_schedule(date, event):
    """新增行程到指定日期"""
    if date not in calendar:
        calendar[date] = []
    calendar[date].append(event)
    print(f"\n已新增行程：{event} 到 {date}！")

def main():
    while True:
        print("\n=== 行事曆功能 ===")
        print("1. 查看行程")
        print("2. 新增行程")
        print("3. 離開")
        choice = input("請選擇操作 (1/2/3): ")

        if choice == "1":
            date = input("請輸入日期 (格式: YYYY-MM-DD): ")
            try:
                datetime.datetime.strptime(date, "%Y-%m-%d")  # 驗證日期格式
                show_schedule(date)
            except ValueError:
                print("日期格式錯誤，請重新輸入！")
        elif choice == "2":
            date = input("請輸入日期 (格式: YYYY-MM-DD): ")
            try:
                datetime.datetime.strptime(date, "%Y-%m-%d")  # 驗證日期格式
                event = input("請輸入行程內容: ")
                add_schedule(date, event)
            except ValueError:
                print("日期格式錯誤，請重新輸入！")
        elif choice == "3":
            print("謝謝使用，行事曆已結束！")
            break
        else:
            print("無效的選項，請重新選擇。")

if __name__ == "__main__":
    main()
