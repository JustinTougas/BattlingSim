from flask import Flask, render_template, request

app = Flask(__name__)

@app.route('/')
def index():
    return render_template('index.html')

@app.route('/food_options', methods=['POST'])
def food_options():
    meal = request.form['meal']
    if meal == "1":
        options = ["Pancakes", "Omelette", "Smoothie", "Yogurt"]
        prompt = "Choose Your Breakfast"
    elif meal == "2":
        options = ["Sandwich", "Salad", "Soup", "Burger"]
        prompt = "Choose Your Lunch"
    elif meal == "3":
        options = ["Steak", "Pasta", "Pizza", "Sushi"]
        prompt = "Choose Your Dinner"
    else:
        options = ["Chips", "Fruit", "Granola Bar", "Cookies"]
        prompt = "Choose Your Snack"
    return render_template('options.html', prompt=prompt, options=options, next_step='/drink_options')

@app.route('/drink_options', methods=['POST'])
def drink_options():
    food = request.form['option']
    meal = request.form['meal']
    if meal == "1":
        options = ["Coffee", "Orange Juice"]
        prompt = "Choose Your Breakfast Drink"
    elif meal == "2":
        options = ["Water", "Iced Tea"]
        prompt = "Choose Your Lunch Drink"
    elif meal == "3":
        options = ["Wine", "Soda"]
        prompt = "Choose Your Dinner Drink"
    else:
        options = ["Milk", "Hot Chocolate"]
        prompt = "Choose Your Snack Drink"
    return render_template('options.html', prompt=prompt, options=options, next_step='/dip_options', food=food)

@app.route('/dip_options', methods=['POST'])
def dip_options():
    drink = request.form['option']
    food = request.form['food']
    dips = {
        "Pancakes": ["Maple Syrup", "Butter"],
        "Omelette": ["Ketchup", "Hot Sauce"],
        "Smoothie": ["Honey", "Granola"],
        "Yogurt": ["Fruit", "Honey"],
        "Sandwich": ["Mayo", "Mustard"],
        "Salad": ["Ranch", "Vinaigrette"],
        "Soup": ["Crackers", "Cheese"],
        "Burger": ["BBQ Sauce", "Ketchup"],
        "Steak": ["Steak Sauce", "Garlic Butter"],
        "Pasta": ["Parmesan", "Chili Flakes"],
        "Pizza": ["Ranch", "Hot Sauce"],
        "Sushi": ["Soy Sauce", "Wasabi"],
        "Chips": ["Salsa", "Guacamole"],
        "Fruit": ["Yogurt", "Nutella"],
        "Granola Bar": ["Peanut Butter", "Honey"],
        "Cookies": ["Milk", "Peanut Butter"]
    }
    options = dips.get(food, [])
    prompt = "Choose Your Dip/Sauce"
    return render_template('options.html', prompt=prompt, options=options, next_step='/summary', food=food, drink=drink)

@app.route('/summary', methods=['POST'])
def summary():
    dip = request.form['option']
    food = request.form['food']
    drink = request.form['drink']
    summary = f"Your order:\nMeal: {food}\nDrink: {drink}\nDip/Sauce: {dip}"
    return render_template('summary.html', summary=summary)

if __name__ == '__main__':
    app.run(debug=True)
