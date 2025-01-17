from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.label import Label
from kivy.uix.textinput import TextInput
from kivy.uix.button import Button
from kivy.utils import get_color_from_hex
import random

class InspirationalApp(App):
    def build(self):
        self.title = "Personality Preditor"  
        self.layout = BoxLayout(orientation='vertical', padding=10, spacing=10)
        self.prompt_input = TextInput(hint_text='Enter your name here', multiline=False, size_hint=(1, 0.2))
        self.layout.add_widget(self.prompt_input)     
        self.generate_button = Button(text='Lets Know about You ?', size_hint=(1, 0.2))
        self.generate_button.bind(on_press=self.generate_message)
        self.layout.add_widget(self.generate_button)
        self.result_label = Label(text='You Really a.............', halign='center', valign='middle', markup=True, font_size=30, size_hint=(1, 0.6))
        self.layout.add_widget(self.result_label)
        return self.layout
    def calculate_numerology_value(self, name):
        numerology_value = sum(ord(char) for char in name)
        return numerology_value  
    def convert_color_to_hex(self, color):
        r = int(color[0] * 255)
        g = int(color[1] * 255)
        b = int(color[2] * 255)
        a = int(color[3] * 255)
        return f"#{r:02X}{g:02X}{b:02X}{a:02X}"
    def generate_message(self, instance):
        name = self.prompt_input.text.strip()
        if not name:
            return
        numerology_value = self.calculate_numerology_value(name)
        responses = [
    ("You have the strength and courage to overcome any obstacle.", (1.0, 0.349, 0.207, 1.0)),  # Orange
    ("You are unique and have a perspective that no one else does.", (0.204, 0.596, 0.859, 1.0)),  # Blue
    ("Your dedication and passion can move mountains.", (0.157, 0.682, 0.376, 1.0)),  # Green
    ("Your ideas and creativity can inspire others around you.", (0.608, 0.349, 0.714, 1.0)),  # Purple
    ("You are capable of achieving greatness.", (0.906, 0.298, 0.235, 1.0)),  # Red
    ("You have the power to change the world.", (0.102, 0.737, 0.612, 1.0)),  # Turquoise
    ("You always find a way to succeed.", (0.953, 0.612, 0.071, 1.0)),  # Orange
    ("You bring positivity wherever you go.", (0.180, 0.800, 0.443, 1.0)),  # Emerald green
    ("Your kindness touches people's hearts.", (0.557, 0.267, 0.678, 1.0)),  # Purple
    ("You make a difference in people's lives.", (0.902, 0.494, 0.133, 1.0)),  # Carrot orange
    ("Your perseverance is an inspiration.", (0.5, 0.5, 1.0, 1.0)),  # Light blue
    ("You have a bright future ahead.", (1.0, 1.0, 0.5, 1.0)),  # Yellow
    ("You light up the room with your smile.", (1.0, 0.87, 0.68, 1.0)),  # Peach
    ("You are a beacon of hope for others.", (0.67, 0.85, 0.9, 1.0)),  # Light cyan
    ("Your talents are limitless.", (0.8, 0.36, 0.36, 1.0)),  # Coral
    ("You have an unstoppable spirit.", (0.72, 0.45, 0.2, 1.0)),  # Sienna
    ("You bring out the best in people.", (0.85, 0.65, 0.13, 1.0)),  # Goldenrod
    ("Your enthusiasm is contagious.", (1.0, 0.75, 0.8, 1.0)),  # Light pink
    ("You have a heart of gold.", (1.0, 0.84, 0.0, 1.0)),  # Gold
    ("You are a ray of sunshine.", (1.0, 1.0, 0.0, 1.0)),  # Bright yellow
    ("Your wisdom is beyond your years.", (0.5, 0.0, 0.5, 1.0)),  # Purple
    ("You have a magnetic personality.", (0.2, 0.8, 0.2, 1.0)),  # Lime green
    ("You exude confidence and grace.", (0.75, 0.0, 0.75, 1.0)),  # Violet
    ("Your generosity is unmatched.", (0.92, 0.78, 0.62, 1.0)),  # Wheat
    ("You have a knack for solving problems.", (0.25, 0.41, 0.88, 1.0)),  # Royal blue
    ("Your creativity knows no bounds.", (0.98, 0.93, 0.36, 1.0)),  # Sunflower
    ("You are a true visionary.", (0.53, 0.81, 0.92, 1.0)),  # Sky blue
    ("Your laughter is the best medicine.", (1.0, 0.92, 0.8, 1.0)),  # Linen
    ("You are the epitome of resilience.", (0.0, 0.5, 0.0, 1.0)),  # Dark green
    ("Your passion is your greatest asset.", (0.96, 0.36, 0.26, 1.0)),  # Firebrick
    ("You see the world in a unique way.", (0.53, 0.81, 0.92, 1.0)),  # Light sky blue
    ("You are a breath of fresh air.", (0.68, 0.85, 0.9, 1.0)),  # Powder blue
    ("Your kindness is a guiding light.", (1.0, 0.87, 0.68, 1.0)),  # Light salmon
    ("You face challenges with unwavering strength.", (0.8, 0.36, 0.36, 1.0)),  # Indian red
    ("You inspire those around you.", (0.5, 0.5, 1.0, 1.0)),  # Cornflower blue
    ("Your presence brings peace and calm.", (0.85, 0.65, 0.13, 1.0)),  # Dark goldenrod
    ("You are a force to be reckoned with.", (0.8, 0.2, 0.2, 1.0)),  # Crimson
    ("Your love is like a warm embrace.", (1.0, 0.5, 0.5, 1.0)),  # Pink
    ("You are a source of endless inspiration.", (0.53, 0.81, 0.92, 1.0)),  # Steel blue
    ("Your potential is limitless.", (0.75, 0.75, 0.75, 1.0)),  # Silver
    ("You make the world a better place.", (0.85, 0.85, 0.1, 1.0)),  # Gold
    ("You are a true gem.", (0.72, 0.45, 0.2, 1.0)),  # Peru
    ("Your spirit is indomitable.", (0.2, 0.8, 0.8, 1.0)),  # Medium turquoise
    ("You have a heart full of love and kindness.", (0.87, 0.63, 0.87, 1.0)),  # Plum
    ("Your spirit is unbreakable.", (0.98, 0.93, 0.36, 1.0)),  # Yellow
    ("You are a true original.", (0.75, 0.2, 0.2, 1.0)),  # Maroon
    ("You uplift others with your kindness.", (0.13, 0.55, 0.13, 1.0)),  # Forest green
    ("You radiate a positive energy.", (0.86, 0.44, 0.58, 1.0)),  # Pale violet red
    ("Your passion lights the way for others.", (0.75, 0.75, 0.75, 1.0)),  # Gainsboro
    ("You are a true blessing to those around you.", (0.5, 0.5, 0.5, 1.0)),  # Gray
    ("Your spirit shines brightly.", (1.0, 0.65, 0.0, 1.0)),  # Orange red
    ("You bring joy and happiness to those you meet.", (0.98, 0.5, 0.45, 1.0)),  # Tomato
    ("Your strength is an inspiration to all.", (0.75, 0.2, 0.2, 1.0)),  # Light coral
    ("You have a beautiful soul.", (1.0, 0.87, 0.68, 1.0)),  # Peach puff
    ("You have the power to make a difference.", (0.8, 0.36, 0.36, 1.0)),  # Indian red
    ("You are a shining example of resilience.", (0.67, 0.85, 0.9, 1.0)),  # Light blue
    ("Your optimism is contagious.", (1.0, 0.92, 0.8, 1.0)),  # Linen
    ("You have an unwavering belief in yourself.", (0.25, 0.41, 0.88, 1.0)),  # Royal blue
    ("You are a beacon of strength.", (0.96, 0.36, 0.26, 1.0)),  # Firebrick
    ("You turn challenges into opportunities.", (0.73, 0.33, 0.83, 1.0)),  # Medium orchid
    ("You have an unstoppable drive to succeed.", (0.94, 0.5, 0.5, 1.0)),  # Light coral
    ("You bring light to even the darkest situations.", (0.74, 0.56, 0.56, 1.0)),  # Rosy brown
    ("Your inner strength is your superpower.", (0.78, 0.78, 0.78, 1.0)),  # Dark gray
    ("You make a difference in everything you do.", (0.99, 0.59, 0.59, 1.0)),  # Light pink
    ("You are a masterpiece in progress.", (0.98, 0.85, 0.45, 1.0)),  # Light gold
    ("Your dreams are worth chasing.", (0.85, 0.65, 0.83, 1.0)),  # Lavender
    ("You are stronger than you realize.", (0.5, 0.25, 0.0, 1.0)),  # Brown
    ("You have the ability to create your own happiness.", (0.2, 0.75, 0.3, 1.0)),  # Emerald green
    ("Your journey is unique and valuable.", (0.7, 0.42, 0.9, 1.0)),  # Medium purple
    ("You have the power to shape your future.", (0.8, 0.99, 0.5, 1.0)),  # Light green
    ("Your voice deserves to be heard.", (0.98, 0.61, 0.47, 1.0)),  # Salmon
    ("You are a work of art, full of potential.", (0.55, 0.48, 0.79, 1.0)),  # Periwinkle
    ("You have an inner light that shines brightly.", (0.85, 0.76, 0.99, 1.0)),  # Thistle
    ("You are capable of achieving your wildest dreams.", (0.69, 0.19, 0.75, 1.0)),  # Orchid
    ("Your heart is full of courage.", (0.5, 0.4, 0.8, 1.0)),  # Slate blue
    ("You are a source of inspiration to many.", (1.0, 0.93, 0.68, 1.0)),  # Light peach
    ("You have the power to overcome fear.", (0.93, 0.51, 0.38, 1.0)),  # Coral
    ("You are a catalyst for change.", (0.1, 0.6, 0.75, 1.0)),  # Teal
    ("Your determination knows no bounds.", (0.93, 0.51, 0.51, 1.0)),  # Light coral
    ("You are a ray of hope in difficult times.", (0.97, 0.95, 0.46, 1.0)),  # Light yellow
    ("You have a heart full of dreams.", (1.0, 0.85, 0.0, 1.0)),  # Golden yellow
    ("You are capable of great things.", (0.96, 0.88, 0.87, 1.0)),  # Misty rose
    ("Your potential is limitless.", (0.75, 0.2, 0.8, 1.0)),  # Medium violet red
    ("You are on a path to success.", (0.93, 0.8, 0.8, 1.0)),  # Light pink
    ("Your creativity is boundless.", (0.54, 0.9, 0.93, 1.0)),  # Pale cyan
    ("You make a positive impact wherever you go.", (0.99, 0.5, 0.7, 1.0)),  # Light salmon
    ("Your kindness is your superpower.", (0.69, 0.37, 0.76, 1.0)),  # Medium orchid
    ("You inspire greatness in others.", (0.9, 0.6, 0.2, 1.0)),  # Gold
    ("You have the courage to pursue your passions.", (0.98, 0.74, 0.84, 1.0)),  # Cotton candy pink
    ("You are capable of turning dreams into reality.", (0.78, 0.36, 0.76, 1.0)),  # Violet
    ("Your positivity creates a ripple effect.", (1.0, 0.8, 0.5, 1.0)),  # Light orange
    ("You are the architect of your destiny.", (0.69, 0.42, 0.88, 1.0)),  # Medium purple
    ("Your enthusiasm is infectious.", (0.78, 0.9, 0.2, 1.0)),  # Light lime
    ("You are worthy of all good things.", (0.99, 0.73, 0.33, 1.0)),  # Peach
    ("You have the strength to keep moving forward.", (0.2, 0.3, 0.7, 1.0)),  # Steel blue
    ("Your journey is just beginning.", (1.0, 0.75, 0.75, 1.0)),  # Light pink
    ("You are deserving of love and respect.", (0.78, 0.14, 0.55, 1.0)),  # Fuchsia
    ("You are a beautiful soul with much to offer.", (0.5, 0.5, 0.9, 1.0)),  # Light slate blue
    ("You are capable of achieving your goals.", (0.9, 0.9, 0.4, 1.0)),  # Lemon chiffon
    ("Your journey inspires others to take action.", (0.3, 0.8, 0.4, 1.0)),  # Sea green
    ("You are a source of strength in challenging times.", (0.25, 0.7, 0.8, 1.0)),  # Light teal
    ("Your heart is full of courage.", (0.98, 0.72, 0.8, 1.0)),  # Light violet
    ("You have the ability to make a difference.", (0.98, 0.49, 0.22, 1.0)),  # Coral
    ("You inspire others with your actions.", (0.75, 0.0, 0.75, 1.0)),  # Purple
    ("You have a gift for uplifting others.", (1.0, 0.98, 0.8, 1.0)),  # Light peach
    ("You bring positivity to every situation.", (0.6, 0.4, 0.2, 1.0)),  # Sandy brown
    ("You are a positive influence on those around you.", (0.0, 0.75, 1.0, 1.0)),  # Sky blue
    ("Your compassion knows no bounds.", (0.99, 0.8, 0.6, 1.0)),  # Peach puff
    ("You have the strength to overcome any challenge.", (0.54, 0.17, 0.89, 1.0)),  # Indigo
    ("You make the world a better place just by being in it.", (0.99, 0.71, 0.41, 1.0)),  # Light orange
    ("You are a warrior, fierce and determined.", (0.9, 0.9, 0.1, 1.0)),  # Light yellow
    ("You bring hope to those in need.", (0.98, 0.36, 0.63, 1.0)),  # Hot pink
    ("You are a fountain of wisdom and knowledge.", (0.8, 0.5, 0.5, 1.0)),  # Light slate gray
    ("You radiate confidence and poise.", (0.33, 0.67, 0.95, 1.0)),  # Light blue
    ("You are an inspiration to everyone you meet.", (0.78, 0.15, 0.65, 1.0)),  # Medium violet
    ("Your heart is as big as the universe.", (0.9, 0.85, 0.0, 1.0)),  # Olive
    ("You are unstoppable in the pursuit of your dreams.", (0.78, 0.8, 0.86, 1.0)),  # Lavender
    ("You have the ability to conquer any fear.", (0.86, 0.64, 0.22, 1.0)),  # Golden yellow
    ("You inspire hope and positivity in others.", (0.8, 0.92, 0.79, 1.0)),  # Light mint
    ("Your kindness is a beautiful gift to the world.", (1.0, 0.45, 0.56, 1.0)),  # Pink
    ("You shine even in the darkest times.", (0.82, 0.33, 0.83, 1.0)),  # Dark orchid
    ("You have the heart of a lion.", (1.0, 0.62, 0.80, 1.0)),  # Light pink
    ("You are a beacon of light and hope.", (0.99, 0.89, 0.63, 1.0)),  # Light yellow
    ("You are a unique and valuable individual.", (0.66, 0.98, 0.8, 1.0)),  # Light sea green
    ("You are destined for greatness.", (0.91, 0.53, 0.74, 1.0)),  # Light violet
    ("You have the strength to rise above challenges.", (0.8, 0.2, 0.8, 1.0)),  # Medium orchid
    ("You are capable of achieving the extraordinary.", (0.94, 0.88, 0.56, 1.0)),  # Pale goldenrod
]

        background_colors = [
            "#2F4F4F",  # Dark Slate Gray
            "#696969",  # Dim Gray
            "#556B2F",  # Dark Olive Green
            "#8B0000",  # Dark Red
            "#2E8B57",  # Sea Green
            "#4B0082",  # Indigo
            "#483D8B",  # Dark Slate Blue
            "#8B4513",  # Saddle Brown
            "#2C3E50",  # Midnight Blue
            "#B22222",  # Firebrick
            "#6A5ACD",  # Slate Blue
            "#4682B4",  # Steel Blue
            "#D2691E",  # Chocolate
            "#228B22",  # Forest Green
            "#A0522D",  # Sienna
            "#5F9EA0",  # Cadet Blue
            "#8A2BE2",  # Blue Violet
            "#7B68EE",  # Medium Slate Blue
            "#6B8E23",  # Olive Drab
            "#00008B",  # Dark Blue
            "#8B008B",  # Dark Magenta
            "#8B4513",  # Saddle Brown
            "#006400",  # Dark Green
        ]   
        response_index = numerology_value % len(responses)
        selected_response, rgba_color = responses[response_index]
        hex_color = self.convert_color_to_hex(rgba_color)
        background_color_hex = random.choice(background_colors)
        background_color = get_color_from_hex(background_color_hex)
        self.result_label.text = f"[color={hex_color}]{selected_response}[/color]"
        self.result_label.font_size = 80
        self.result_label.canvas.before.clear()
        with self.result_label.canvas.before:
            from kivy.graphics import Color, Rectangle
            Color(*background_color)
            self.bg_rect = Rectangle(size=self.result_label.size, pos=self.result_label.pos)
        self.result_label.bind(size=self.update_rect, pos=self.update_rect)
    def update_rect(self, *args):
        self.bg_rect.size = self.result_label.size
        self.bg_rect.pos = self.result_label.pos
if __name__ == "__main__":
    InspirationalApp().run()
