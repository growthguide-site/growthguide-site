import zipfile
import os

# Directory and file names
base_dir = "/mnt/data/growthguide_site"
os.makedirs(base_dir, exist_ok=True)

# Main HTML files (from the user's website design)
filenames = [
    "index.html",
    "channel-management.html",
    "editing-automation.html",
    "growth-strategy.html",
    "faq.html",
    "why-us.html"
]

# Placeholder content for all files except index.html (which already exists in canvas)
page_content = {
    "channel-management.html": "<h1>Channel Management</h1><p>[Full 30,000-word content here]</p>",
    "editing-automation.html": "<h1>Editing & Automation</h1><p>[Full 30,000-word content here]</p>",
    "growth-strategy.html": "<h1>Growth Strategy</h1><p>[Full 30,000-word content here]</p>",
    "faq.html": "<h1>Frequently Asked Questions</h1><p>[All FAQ content goes here]</p>",
    "why-us.html": "<h1>Why Choose GrowthGuide?</h1><p>[All detailed reasons and value propositions]</p>"
}

# Write the placeholder content to the appropriate HTML files
for name, content in page_content.items():
    with open(os.path.join(base_dir, name), "w") as f:
        f.write(f"<!DOCTYPE html><html><head><meta charset='UTF-8'><title>{name}</title></head><body>{content}</body></html>")

# Save the main index.html file (from canvas)
index_html_path = os.path.join(base_dir, "index.html")
with open(index_html_path, "w") as f:
    f.write("""<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="description" content="GrowthGuide - YouTube Channel Automation, Editing, and Management Services">
  <title>GrowthGuide | YouTube Automation & Channel Management</title>
  <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&display=swap" rel="stylesheet">
  <style>
    body {
      margin: 0;
      font-family: 'Inter', sans-serif;
      background-color: #f9fafb;
      color: #1e2a38;
    }
    header {
      background: linear-gradient(to right, #3D8BFF, #8754FF);
      padding: 2rem;
      text-align: center;
      color: white;
    }
    nav a {
      margin: 0 1rem;
      color: white;
      text-decoration: none;
      font-weight: 600;
    }
    .hero {
      padding: 4rem 2rem;
      text-align: center;
      background-color: #ffffff;
    }
    .hero h1 {
      font-size: 3rem;
      margin-bottom: 1rem;
    }
    .hero p {
      font-size: 1.2rem;
      color: #555;
    }
    .section-link {
      text-align: center;
      padding: 2rem;
      background-color: #f0f4f8;
    }
    .section-link a {
      display: block;
      margin: 1rem auto;
      padding: 1rem 2rem;
      background-color: #3D8BFF;
      color: white;
      border-radius: 8px;
      text-decoration: none;
      font-weight: 600;
      max-width: 300px;
    }
    footer {
      background-color: #1e2a38;
      color: #fff;
      text-align: center;
      padding: 2rem;
    }
    .socials a {
      margin: 0 0.5rem;
      color: #fff;
      text-decoration: none;
    }
  </style>
</head>
<body>
  <header>
    <h1>GrowthGuide</h1>
    <nav>
      <a href="index.html">Home</a>
      <a href="channel-management.html">Channel Management</a>
      <a href="editing-automation.html">Editing & Automation</a>
      <a href="growth-strategy.html">Growth Strategy</a>
      <a href="faq.html">FAQs</a>
      <a href="why-us.html">Why Us</a>
    </nav>
  </header>

  <section class="hero">
    <h1>Automate, Grow, and Scale Your YouTube Channel</h1>
    <p>We manage your channel from A to Z: editing, automation, strategy, and growth—all done for you.</p>
  </section>

  <section class="section-link">
    <h2>Explore Our Services</h2>
    <a href="channel-management.html">Channel Management</a>
    <a href="editing-automation.html">Editing & Automation</a>
    <a href="growth-strategy.html">Growth Strategy</a>
    <a href="faq.html">Frequently Asked Questions</a>
    <a href="why-us.html">Why Choose GrowthGuide?</a>
  </section>

  <footer id="contact">
    <h3>Connect with us</h3>
    <div class="socials">
      <a href="https://discord.com/users/growthguide_" target="_blank">Discord</a>
      <a href="https://www.instagram.com/growth_guide11" target="_blank">Instagram</a>
      <a href="https://x.com/@growthguide121" target="_blank">Twitter</a>
      <a href="https://t.me/growthguide13" target="_blank">Telegram</a>
    </div>
    <p>&copy; 2025 GrowthGuide. All rights reserved.</p>
  </footer>
</body>
</html>""")

# Create ZIP file
zip_path = "/mnt/data/growthguide_website.zip"
with zipfile.ZipFile(zip_path, 'w') as zipf:
    for root, dirs, files in os.walk(base_dir):
        for file in files:
            zipf.write(os.path.join(root, file), arcname=file)

zip_path

