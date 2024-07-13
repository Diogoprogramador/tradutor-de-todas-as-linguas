# tradutor-de-todas-as-linguas
import tkinter as tk
from googletrans import Translator


class TranslatorApp:
    def __init__(self, root):
        self.root = root
        self.root.title("Translator")

        self.label = tk.Label(self.root, text="Texto a ser traduzido:")
        self.label.pack()

        self.text_entry = tk.Text(self.root, height=5, width=50)
        self.text_entry.pack()

        self.translate_button = tk.Button(self.root, text="Traduzir", command=self.translate_text)
        self.translate_button.pack()

        self.result_label = tk.Label(self.root, text="Tradução:")
        self.result_label.pack()

        self.translation_output = tk.Text(self.root, height=5, width=50)
        self.translation_output.pack()

    def translate_text(self):
        translator = Translator()
        input_text = self.text_entry.get("1.0", "end-1c")
        translation = translator.translate(input_text, dest='pt')
        self.translation_output.delete("1.0", "end")
        self.translation_output.insert("1.0", translation.text)


if __name__ == "__main__":
    root = tk.Tk()
    app = TranslatorApp(root)
    root.mainloop()
