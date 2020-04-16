# Coronavirus Answers

JSON API for [Coronavirus FAQ](https://faq.coronavirus.gov)

## Why

Many websites will want to include information about Coronavirus and will want to make sure their information is accurate and up-to-date.

The US Government is maintaining a repository of questions and answers available at https://faq.coronavirus.gov.

The goal of this project is provide an API for anyone who wishes to incorporate that information onto their site so that they always have the most accurate and up-to-date information available.

## How to use it

The API consists of two endpoints that serve JSON. One contains the complete list of categories. The other contains the complete list of answers.

### Endpoints

The answers endpoint is available at [`https://nyc-cto.github.io/coronavirus-answers/answers.json`](https://nyc-cto.github.io/coronavirus-answers/answers.json) and returns a JSON array containing all of the answer objects.

The category endpoint is available at [`https://nyc-cto.github.io/coronavirus-answers/categories.json`](https://nyc-cto.github.io/coronavirus-answers/categories.json) and returns a JSON array containing all of the category objects. The category objects are sorted in the same order as they appear on the home page of [Coronavirus FAQ](https://faq.coronavirus.gov).

### Answer data

An answer object represents an answer about Coronavirus.

#### Example
```json
{
  "title": "Where can I find additional information about water transmission and COVID-19?",
  "category": "water-transmission",
  "excerpt": "Water transmission and COVID-19",
  "source": "CDC",
  "source_url": "https://www.cdc.gov/coronavirus/2019-ncov/php/water.html",
  "url": "https://faq.coronavirus.gov/water-transmission/additional-information-about-water-transmission-and-covid-19/",
  "promoted": false,
  "date": "2020-03-10",
  "content": "<ul>  <li><a href=\"https://www.cdc.gov/healthywater/global/sanitation/workers_handlingwaste.html\">CDC: Guidance for reducing health risks to workers handling human waste or sewage</a></li> </ul>"
}
```

#### Attributes

title: the question. Human-readable text.

category: the name of the category this answer belongs to. A URL-safe string.

excerpt: the category name. Human-readable text. This data is not displayed on the Coronavirus FAQ page and it is recommended that you ignore it.

source: the name of the source for this answer. Human-readable text.

source_url: a URL pointing to the definiative source of the answer.

promoted: Promoted answers are listed on the hompage in the section for their category. Other answers are only listed on the category page. Boolean.

date: date this answer was last updated. ISO 8601 format.

content: content of the answer. An HTML fragment

### Category data

A category object represents an answer category.

#### Example
```json
{
  "banner": {
   "heading": "CDC issues Domestic Travel Advisory.",
   "content": "Employees of critical infrastructure, as <a href='https://www.cisa.gov/publication/guidance-essential-critical-infrastructure-workforce'>defined by the Department of Homeland Security</a>, have a special responsibility to maintain normal work schedule."
  },
  "title": "Traveling",
  "name": "travel",
  "url": "https://faq.coronavirus.gov/travel/"
}
```

#### Attributes

title: title of the category. Human-readable text.

name: unique identifier for the category. URL-safe string.

url: the canonical URL to this category on https://faq.coronavirus.gov.

banner: an optional banner object for the category.

Categories only include a banner object if they have a banner that should be displayed. The underlying data includes banner data for all categories, but in most cases it is placeholder data and should be ignored.

### Banner

A banner object represents information that is displayed as a banner with the category.

#### Example
```json
{
  "heading": "CDC issues Domestic Travel Advisory.",
  "content": "Employees of critical infrastructure, as <a href='https://www.cisa.gov/publication/guidance-essential-critical-infrastructure-workforce'>defined by the Department of Homeland Security</a>, have a special responsibility to maintain normal work schedule."
}
```

heading: the heading or title for the banner. Human-readable text.

content: the content for the banner. An HTML fragment.

## Development

This project is released under the MIT License. By contributing to this project you agree to license your contributions under those terms.

This project is built on [Jekyll](https://jekyllrb.com), a static site generator.

### Updating content

Category data is stored in Markdown files in the `_categories` directory.

Answer data is stored in Markdown files in the `_data` directory.

The paths and formats correspond exactly with the data files that generate the [Coronavirus FAQ](https://faq.coronavirus.gov/) website. To update this project's content, replace those two directories with the directories from that project.

### Running locally

1. Install Ruby
2. Install Jekyll and Bundler, `gem install jeykll bundler`
3. Run the development server `jekyll serve`
4. View the site at [`http://localhost:4000`](http://localhost:4000)

The development server will watch for changes to the code and regenerate the site when they are made.

## Deploying

This project is deployed via [GitHub Pages](https://pages.github.com)

## Limitations

The primary limitation is that there is no way for this project to automatically remain up-to-date with data from [Coronavirus FAQ](https://faq.coronavirus.gov/). This repo will be kept up to date with periodic pushes to match the canonical source, however an automated approach is being investigated.

## Future work

### Incorporate into Coronavirus FAQ site

This project should not exist.

The API endpoints should be a part of the Coronavirus FAQ project.

That would require copying the `answers.json` and `categories.json` into the Coronavirus FAQ codebase. Unfortunately, that codebase is not publicly available.

### Automated testing

Automated tests can ensure the endpoints return valid JSON, in the documented structure, and with the correct data.

### Automated checking for updates

An automated system can check for updates to the Coronovirus FAQ page. That way, someone with access to their codebase can be notified to update the data in this project.

### Automated updating

When the Coronavirus FAQ page changes, an automated system could then update the data on this project. This would require access to the Coronavirus FAQ repository to implement.

## Contributors

[Damien Burke](https://github.com/exmember)

[Rob Head](https://github.com/roberthead)

### Special thanks

[Megan Folsom](https://github.com/mfolsom)

[Jordan Epps](https://github.com/jkepps)

[Justin Man](https://github.com/jisaf)

[NYC Mayor's Office of the Chief Technology Officer](http://nyc.gov/cto/)

[Talaria Software](https://www.talariasoftware.com)
