
# Fixes and how to's
## Korrupt database
Feilmeldingen sier at mySQL har blitt avsluttet på feil måte. Mest sannsynligvis at jeg har slått av pc med prosesser gående. 

>Hvis dere får dette problemet (lokalt, dette skjer ikke i prod) så må dere følge denne videoen:
> https://www.youtube.com/watch?v=84IOtc05TuA](https://www.youtube.com/watch?v=84IOtc05TuA)

---
## Make Cross
### Step 1: Create the Basic Layout
 Open Elementor
	- Go to your WordPress Dashboard → Pages → Click Edit with Elementor on the page where you want the design.
- Add a Two-Column Section
	- Click the "+" button to add a new section
	- Choose the two-column structure
	- Adjust the left column width (e.g., 30%) and right column width (e.g., 70%) to match the design.
- Add Content to Each Column
	- In the left column add a Heading Widget (e.g., "OM") and Text Editor Widget (e.g., "Neal Ashley Contrad").
	- In the right column, add an Image Widget (for the eyes icon) and some Text Widgets for the description.
	- Below that, add a Contact Form Widget (if you are using a plugin like WPForms or Elementor Forms).

---
### Step 2: Add the Horizontal Line
- Drag a Divider Widget
	- Find the Divider Widget in Elementor.
	- Drag it above the two-column section (at the top, spanning across both columns).
	- Style the Divider
- Go to the Content tab in the left panel:
	- Set Width to 100%.
	- Set Weight to 1px (or adjust for a thicker line).
	- Set Alignment to Center.
- Go to the Style tab:
	- Change Color to Black (#000000).
	- Change Gap to 0 (so it sticks to the section).
---
### Step 3: Add the Vertical Line
- Drag Another Divider Widget
	- Add another Divider Widget but place it inside the left column (where the "OM" text is).
	- Make it Vertical Using Rotation
- In the Content tab:
	- Set Width to 2px (or adjust as needed).
	- Set Height to 100px (or more, depending on how tall you want the vertical line).
- In the Advanced tab → Custom Positioning
	- Set Position to Absolute
	- Set Vertical Orientation to Middle.
	- Adjust the left margin to position it correctly.
---
### Step 4: Adjust Spacing for Proper Alignment
- Set Column Padding/Margin
- Click on the Left Column → Advanced Tab:
	- Add Padding on the right side (to create spacing from the vertical line).
- Click on the Right Column → Advanced Tab:
	- Add Padding on the left side (to ensure text doesn’t touch the vertical line).
- Check Mobile Responsiveness
	- Click the Responsive Mode icon at the bottom.
	- Switch between Tablet and Mobile views.
	- Adjust margins/padding if needed.
---
### Step 5: Save and Publish
- Click Update to save changes.
- Preview the page to make sure the lines align correctly.
---
### Optional: Alternative Adjustments
- If the vertical line is not long enough, increase its Height.
- If you want more control, use Custom CSS (see Method 3).
- For more styling, add a Box Shadow to the section for depth.
- Now, you should have a clean crossing line structure that looks like the design in your image!
---
## Make custom roles
Follow the video below:

> [!important] NOTE!
> It is important to check off "edit_theme_options" so the user can edit menus.


[![https://www.youtube.com/watch?v=_HE875kKo3k](https://www.youtube.com/watch?v=_HE875kKo3k "https://www.youtube.com/watch?v=_HE875kKo3k")]

---
## Migrate Website - phpMyAdmin
- Last ned /wp-content og we-config.php fra ønsket side
- Backup site files via File Manager
- Export the site database via phpMyAdmin
---
- Transfer site to new domain 
	- create a database for the new domain (if dont exist)
	- create a domain/subdomain (if dont exist)
	
	- Install Wordpress at new domain
	- Import site database via phpMyAdmin (edit database name and use if needed)
	- Go to {dbname}_options and change siteurl and home to correct address
	- Delete tables from default db (dev)
	
	- Upload/replace wp-content folder in File Manager
	- Update config.php file with correct details
	- Find and replace all image/file paths to new URL
---
## Migrate website to Hostinger
- Add website
	- Wordpress
- Credentials
	- use theme in stead
- Select default theme (2025)
	- Do not install plugins!
- Use temporary domain ("wp is installing")
- Select dashboard to new website in hostinger
- go to "databases"
	- Check info
- goto phpMyAdmin 
	- wp_options - Set correct "home" and "siteurl" (url of new website)
---
## The Blank Page Problem
- Delete default pages, create new ones and make sure to "edit with elementor" 
- Set the page template to "Elementor canvas" (can also be done from quick edit)  
	- Create: Home - slug = home - template = Elementor canvas 
	- Create: About - slug = about - template = Elementor canvas 
- Go to Settings
	- Click readings
	- Change your homepage displays from "Your latest post" to "A static page" and Choose your page
	- Choose which page you want to set as home page and save changes 
---
## The_Content
- First in order to fix the infamous "the_content" error you must download twenty nineteen theme, then go to wherever the theme is.
- When doing this locally it will be in "C:\xampp\htdocs\wordpress\wp-content\themes\twentynineteen"
- Here you can find the index.php file and on a line above <?php get_footer; ?> you must write: <?php the_content; ?>
---

[^1]: To find the correct url:
	- Go to github.com, click your profile picture and select "Your Profile".
	- Select "Repository" and hit the green "New" button
	- Set a repo -name, and set the desired settings and click "Create Repository"
	- Then, go to the new repository, click "Code..", select the "local" -tab, and select "Https" (or SSH, obviusly) - That's the correct URL 

[^2]: Add the '-u' -flag for comprehensive status
