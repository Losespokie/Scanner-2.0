# Scanner-2.0
A simple HTML + CSS + JavaScript project.  Uses Open AI DALLIER API to generate AI images. 
from PIL import Image, ImageDraw, ImageFont

# Image Configuration
image_size = (892, 331)
background_color = (255, 255, 255)  # White
text = "Remetly"
text_color = (0, 153, 153)  # Teal-like

# Create blank image
img = Image.new("RGB", image_size, background_color)
draw = ImageDraw.Draw(img)

# Load a font (fallback to default if unavailable)
try:
    font = ImageFont.truetype("DejaVuSans-Bold.ttf", 76)
except:
    font = ImageFont.load_default()

# Calculate centered text position
text_bbox = draw.textbbox((0, 0), text, font=font)
text_width = text_bbox[2] - text_bbox[0]
text_height = text_bbox[3] - text_bbox[1]
position = ((image_size[0] - text_width) // 2, (image_size[1] - text_height) // 2)

# Draw the text
draw.text(position, text, font=font, fill=text_color)

# Save the image
img.save("remetly.png")

print("✅ Image saved as remetly.png")
