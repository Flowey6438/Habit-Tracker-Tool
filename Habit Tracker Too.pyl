import json
from datetime import datetime

DATA_FILE = "habit_tracker.json"

def load_data():
    try:
        with open(DATA_FILE, "r", encoding="utf-8") as file:
            return json.load(file)
    except (FileNotFoundError, json.JSONDecodeError):
        return {}

def save_data(data):
    with open(DATA_FILE, "w", encoding="utf-8") as file:
        json.dump(data, file, indent=4)

def add_habit(data, habit):
    if habit not in data:
        data[habit] = []
        print(f"已添加新习惯：{habit}")
    else:
        print("该习惯已存在。")

def record_habit(data, habit):
    if habit in data:
        today = datetime.now().strftime("%Y-%m-%d")
        if today not in data[habit]:
            data[habit].append(today)
            print(f"已为习惯 {habit} 打卡成功！")
        else:
            print(f"今天已经为 {habit} 打过卡了。")
    else:
        print("习惯未找到，请先添加该习惯。")

def view_stats(data):
    for habit, dates in data.items():
        print(f"\n习惯: {habit}")
        print(f"打卡次数: {len(dates)}")
        if dates:
            print(f"最近打卡日期: {max(dates)}")
        else:
            print("还没有打卡记录。")

if __name__ == "__main__":
    data = load_data()
    print("欢迎使用习惯追踪器！")

    while True:
        print("\n请选择一个操作：")
        print("1. 添加新习惯")
        print("2. 记录习惯打卡")
        print("3. 查看习惯统计")
        print("4. 退出")

        choice = input("请输入选项（1/2/3/4）：")

        if choice == "1":
            habit = input("请输入要追踪的新习惯名称：")
            add_habit(data, habit)
            save_data(data)
        elif choice == "2":
            habit = input("请输入要记录的习惯名称：")
            record_habit(data, habit)
            save_data(data)
        elif choice == "3":
            view_stats(data)
        elif choice == "4":
            print("感谢使用习惯追踪器，再见！")
            break
        else:
            print("无效选项，请重新选择。")
