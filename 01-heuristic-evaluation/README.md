# Heuristic Evaluation: polito.it (Education section)

A usability review of the Politecnico di Torino website, seen through the eyes of a prospective international master's applicant.

## Context

- **Evaluated:** the English version of polito.it, mainly the *Education* section
- **Persona:** an international student, new to Italy, who wants to apply to a master's programme
- **Why this site:** I study at Politecnico di Torino and use the site often, so I could judge which problems are real

## Method

- **Technique:** heuristic evaluation with Nielsen's 10 usability heuristics
- **Evaluator:** one person (me), so findings are expert opinion, not user data
- **Tasks:**
  1. Find the application requirements and deadline for a master's programme
  2. Find tuition fees and scholarship information
  3. Switch the site to English and find the same information
  4. Find a way to contact the university about an application question
- **Severity scale:** 1 = cosmetic, 2 = minor, 3 = major, 4 = critical (user may not complete the task)
- **Tools:** Chrome (desktop and mobile emulation), Lighthouse for a separate technical check

## Summary

The site is technically solid: accessibility 97, best practices 100. The problems I found are about **information architecture and content**: the same topic lives in several places, key terms are never explained, and some English pages contain Italian. Automated tools cannot detect these, which is why a manual review is needed.

Most serious finding: a new student looking for scholarships ends up on a page with no filter for prospective students, while the main state scholarship (EDISU) is hidden behind a term that is never explained.

## Findings

| # | Finding | Heuristic | Severity |
|---|---|---|---|
| 1 | Master's programme information sits in three places, and two links share the same name but lead to different pages | #4 Consistency, #6 Recognition over recall | 3 |
| 2 | Scholarship search has no "prospective student" option; EDISU (the main state scholarship) is unexplained | #2 Match with real world, #3 User control, #6 Recognition over recall | 4 |
| 3 | The scholarships topic exists in two different parts of the site, with different menus | #4 Consistency, #1 Visibility of system status | 3 |
| 4 | English pages contain Italian content (scholarship announcements) | #2 Match with real world | 3 |
| 5 | Contact is hard: no direct email, only a ticket system, and choosing the right ticket category is unclear | #10 Help, #5 Error prevention | 3 |
| 6 | Menu says "Financial aid" but the page title is "Tuition fees, services and other opportunities" | #4 Consistency | 2 |
| 7 | The Financial aid page has seven boxes that each open a separate page, with no summaries | #7 Efficiency, #8 Minimalist design | 2 |
| 8 | The top menu and the blue banner repeat the same section titles, and some labels are long and in capitals | #8 Minimalist design | 2 |

### Finding 1: Two "Master's degree programmes" paths

The first two paths start from the *Education* menu, but they lead to different content.

- **Path A:** Applying, studying, graduating → Master's degree programmes. Application steps for Italian and non-Italian qualifications.
- **Path B:** Education → Master's degree programmes. A searchable catalogue of programmes with language filter.
- **Path C:** Education → International students → Prospective students → Master's degree programmes admission and enrolment. A third, similarly named entry. I did not compare its content with Path A, so they may overlap.

An applicant can easily open the wrong one. **Suggestion:** rename them by purpose, for example "Programme catalogue" and "How to apply".

![Education menu](images/01-education-menu.png)
![Programme catalogue](images/02-master-programmes-catalogue.png)

### Finding 2: The scholarship dead end

On the *Scholarships and Awards* page, the "Target group" filter offers *All*, *Current students* and *Graduates*. There is no option for new or prospective students. The main state scholarship is under **EDISU**, a box on the Financial aid page, and nothing explains what EDISU is. A newcomer finds it only by elimination, because the other boxes are not about scholarships.

The *International students* side menu does have a "Prospective students" section, but it only covers who counts as a prospective student, admission and enrolment (Bachelor's, Master's) and services for international applicants. Financial aid is a separate section next to it, so a prospective student has to know to look there.

**Click count** (Education opens on hover, so it is not counted; the back click is counted):

| Path | Steps | Clicks |
|---|---|---|
| Actual | International students → Financial aid → Scholarships and awards → Target group filter → Back → EDISU | 6 |
| Ideal | International students → Financial aid → EDISU | 3 |

Six is a minimum: a user who does not know what EDISU is would probably also open other boxes first.

**Suggestions:**
- Add a "Prospective students" option to the Target group filter
- Add a one-sentence explanation to the EDISU box, for example "Regional scholarship for eligible students"

![Financial aid page](images/03-financial-aid-desktop.png)
![Target group filter](images/04-scholarships-and-awards-filter.png)
![Prospective students section](images/08-prospective-students.png)

### Finding 3: One topic, two places

From *Financial aid* (under International students), the button "Scholarships and awards" sends the user to a page under *Services and life at Politecnico → Right to education and tuition fees*. The breadcrumb and side menu change completely, and the international students context is lost.

### Finding 4: Italian content on the English site

The site structure and menus are the same in both languages, but on the English *Scholarships and Awards* page the announcement titles (for example "Bando di selezione per tre borse di studio...") and the announcements themselves are in Italian. These announcements are aimed at students with foreign qualifications, who are the people least likely to read Italian.

![Italian titles](images/05-scholarships-italian-titles.png)

### Findings 5 to 8

- **5. Contact.** There is no direct email address. The ticket form asks for a category, and picking the right one is not easy for someone who does not know the university's internal structure.
- **6. Label mismatch.** The menu item "Financial aid" opens a page titled "Tuition fees, services and other opportunities", so users cannot confirm they are in the right place.
- **7. Seven separate boxes.** Each box on the Financial aid page opens another page. **Suggestion:** use expandable summaries (accordions) so a user can read two or three sentences before leaving the page. The site already uses this pattern for scholarship announcements lower on the same page.
- **8. Repeated navigation.** The same ten section titles appear in the top menu and in the blue banner. Long labels such as "Specializing Master's programmes and lifelong learning" take up to four lines.

## What works well

- The site structure and menus are identical in Italian and English
- The programme catalogue cards show language (ITA/ENG), campus and international opportunities at a glance
- On mobile, a "Navigate this section" expandable menu sits at the top of the page, and the layout stays readable. The desktop version hides the same navigation in a side panel that is easy to miss, so the mobile pattern could be reused
- The page code includes a "skip to main content" link for keyboard and screen reader users

![Mobile view](images/06-financial-aid-mobile.png)

## Technical check (Lighthouse)

Page: `/en/education/international-students/financial-aid`, mobile emulation in Chrome DevTools, incognito window. Lab data from one page and one run, so results may vary.

| Category | Result |
|---|---|
| Performance | 75 |
| Accessibility | 97 |
| Best practices | 100 |
| SEO | 85 |
| Agentic browsing | 2/2 passed (informational, not a 0 to 100 score) |

| Metric | Value |
|---|---|
| First Contentful Paint | 2.8 s |
| Largest Contentful Paint | 5.3 s (poor) |
| Total Blocking Time | 70 ms |
| Cumulative Layout Shift | 0.068 |
| Speed Index | 2.8 s |

**Issues reported:**
- Performance: slow Largest Contentful Paint is the main reason for the score of 75
- SEO: the page has no meta description, and two links have no descriptive text
- Accessibility: links such as the breadcrumb are distinguishable by colour alone

![Lighthouse results](images/07-lighthouse-results.png)

## Top three recommendations

1. Add a "Prospective students" filter to the scholarship search and explain EDISU (findings 2 and 3)
2. Give the two "Master's degree programmes" links different names (finding 1)
3. Translate the scholarship announcements for the English site, or mark clearly that they are Italian only (finding 4)

## Limitations

- One evaluator and one persona. Real users, tested with a usability study, would likely find more problems and could disagree with some of my severity ratings.
- Lighthouse was run on one page only.
- I evaluated the Education section, not the whole site.
