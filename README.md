# Extended Education Org Chart

Welcome to the Extended Education Org Chart! The aim is to keep this as simple as possible to maintain: 99% of the time, the only file that should need to be updated is [this one](https://github.com/ExtendedEducation/org-chart/blob/master/misc/data.csv). 

## Giving editing access to someone new

This must be done by someone with full access (currently Hayley and Louise).

1. Click the 'Settings' link in the github menu bar (or [click here](https://github.com/ExtendedEducation/org-chart/settings/access).)
2. Under 'manage access' click 'add people'.
3. Type in their email address, then click on it.
4. Select 'write' access, then 'Add selection'.
5. This will invite them to create a github account, then give them editing access to the repository.

## To add new members to the team

Add each new member as a new line, in the following format, with no spaces between the commas or at the end of the line:

> ID number of new staff member (these can just increase sequentially),Full Name,ID number of the staff member's line manager,Job Title (surrounded in quote marks if it includes commas or ampersands),Department,Email,Info

The 'info' field is for a very very short description of responsibility.

So, for instance:

> 2,Philippa Swindell,1,"Associate Director, Commercial Operations & Planning",SLT,p.r.swindell@lse.ac.uk,"Operations & transformation strategy and oversight"

## Update members of the team

If a team member leaves (and is replaced by someone else), or their job title or reporting line changes, simply change the entry in the existing list. 

Lines can be deleted if the role is no longer required (but if the person is a line manager, make sure you change the reporting lines of their team as well).

## Adding a new Department

New departments can be added at any time, but require a (small!) amount of coding knowledge. 

First, decide the one word name of the department (eg 'Operations', 'Transformation', etc). 

There are three main steps involved:

### Add the colour coding

1. Choose a colour for your new department and identify the [hex code](https://htmlcolorcodes.com/).
2. Open the [CSS file](https://github.com/ExtendedEducation/org-chart/edit/master/misc/style.css)
3. New code will need to be added in two places. The first is at the top of the CSS file, where you will see a list of departments, ie: 

```
.Summer {
  background-color: #B91372 !important;
}
```

Copy this, paste it back into the file, and then change the name (ie '.Summer') and the hex code (ie '#B91372') to your new values. The department name should be capitalised.

4. Scroll further down the CSS file to find the list of attributes that are in the format '.department-slt'. You will repeat the process from earlier, changing the attribute name (the department name should be in lowercase this time), and the hex code.
5. Save the css file.

### Create the new template page

1. Copy the code in [this](https://github.com/ExtendedEducation/org-chart/blob/master/template) page.
2. Create a new page in the main directory of the repository, calling it 'departmentname.html', and paste the contents of the template into it.
3. Scroll down to line 47 and change 'DEPARTMENT NAME' to the name of your new department.
4. On the same line, make sure that you are also including the individual IDs of the reporting line from the top of Extended Education down to this department. For instance:

```
if( d["Department"] == "Transformation" || d["id"] == 2 || d["id"] == 1)
```

In code-speak, this translates to: 

> In the data.csv file, if a person has a 'Department' of 'Transformation' OR an ID of 2 OR an ID of 1, include them in this chart. This, in this case, it would include everyone in the 'Transformation' team, plus Philippa (ID 2) and Elizabeth (ID 1).

Additional parameters could be added with the || separation - for instance: 

```
if( d["Department"] == "Transformation" || d["Department"] == "Operations" || d["id"] == 2 || d["id"] == 1)
```

Thus, this would include people in the Transformation department, the Operations department, plus Philippa and Elizabeth. 

5. Save your new department.

### Edit the the navigation page

To simplify updates, the navigation and buttons at the bottom of each chart are saved to a single page, then imported into each of the charts. 

1. Open the [include.html](https://github.com/ExtendedEducation/org-chart/edit/master/include.html) page in edit mode.
2. Add a new line in the < div class="departments"> section:

If, for instance, I'm adding a 'Technology' team:

Old:

```
  <div class="departments">
    <a class="department department-slt" href="https://extendededucation.github.io/org-chart/slt.html">Senior Leadership Team</a>
    <a class="department department-transformation" href="https://extendededucation.github.io/org-chart/transformation.html">Transformation Team</a>
    <a class="department department-operations" href="https://extendededucation.github.io/org-chart/operations.html">Operations Team</a>
    <a class="department department-programmes" href="https://extendededucation.github.io/org-chart/programmes.html">Programmes Team</a>
    <a class="department department-marketing" href="https://extendededucation.github.io/org-chart/marketing.html">Marketing Team</a>
    <a class="department department-summer" href="https://extendededucation.github.io/org-chart/summer.html">Summer Team</a>
    <a class="department" href="https://extendededucation.github.io/org-chart/full-chart.html">Extended Education</a>
  </div>
```

New: 

```
  <div class="departments">
    <a class="department department-slt" href="https://extendededucation.github.io/org-chart/slt.html">Senior Leadership Team</a>
    <a class="department department-transformation" href="https://extendededucation.github.io/org-chart/transformation.html">Transformation Team</a>
    <a class="department department-operations" href="https://extendededucation.github.io/org-chart/operations.html">Operations Team</a>
    <a class="department department-programmes" href="https://extendededucation.github.io/org-chart/programmes.html">Programmes Team</a>
    <a class="department department-marketing" href="https://extendededucation.github.io/org-chart/marketing.html">Marketing Team</a>
    <a class="department department-summer" href="https://extendededucation.github.io/org-chart/summer.html">Summer Team</a>
    <a class="department department-technology" href="https://extendededucation.github.io/org-chart/technology.html">Technology Team</a>
    <a class="department" href="https://extendededucation.github.io/org-chart/full-chart.html">Extended Education</a>
  </div>
```

Save the file. 

### Update the data.csv file to change the department of any relevant individuals. 

And then you're done!
