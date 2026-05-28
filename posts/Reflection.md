---
title: Reflection
date: 2026-05-28
author: Xi Lin
summary: This final reflection evaluates the development of EASY DIVE, focusing on how the prototype responded to the original design goals, what changed during the process, and what I learned from building and testing the web app.
tags:
  - Reflection
  - Evaluation
  - Design Iteration
---
When I look back at the final version of EASY DIVE, I think the project was successful in turning my original idea into a working web application prototype rather than only a visual interface. My initial goal was to design a lightweight social platform for divers, where users could record dive conditions, browse community information, view local dive shops, and manage a basic diver profile. The final prototype includes these core areas through five main sections: Home, Log Dive, Explore Sites, Dive Shops, and Profile. It also includes a demo login, backend routes, structured data, dynamic cards, search filters, a live log preview, and profile editing. Because of this, the final result feels closer to a real web system than I expected at the beginning of the project.

In terms of performance and technical behaviour, the strongest part of the application is that most interactions feel immediate after the app has loaded. Page navigation is handled on the front end by switching between different page sections, so moving between Home, Log Dive, Explore Sites, Dive Shops, and Profile does not require a full page reload. This makes the prototype feel smooth and app-like. As shown in Appendix A, the main local task walkthrough could be completed without the page freezing or needing to reload. The Explore Sites page also performs efficiently for the current dataset because the site and log data are loaded once, then filtered on the client side. For a small prototype, this was a reasonable technical decision because it keeps the search interaction fast and avoids repeated backend requests for every filter change.

The Log Dive page also performs well during normal use. The live preview updates as the user changes the form inputs, which gives immediate feedback before saving. This became one of the most useful interaction features in the final prototype because it helps the user understand what their saved log will look like. The save process also works as a complete technical flow: the user fills in the form, submits it, the data is sent to the backend API, the record is inserted into the database, and the log list updates afterwards. This shows that the project is not only displaying static content, but also responding to user input.

However, the same technical structure also creates weaknesses. Compared with a static HTML, CSS, and JavaScript site, EASY DIVE is more complex because it uses MojoJS routes, API endpoints, and a local database through sql.js. This makes the prototype more realistic, but it also makes setup and deployment harder. The app needs npm install, npm start, and a local server running on port 3000. This means it is less accessible to someone who simply wants to open a webpage. If I had more time, I would improve the README with clearer setup instructions, screenshots of the expected running state, and common troubleshooting notes. I would also test the deployment pathway more carefully, because a system that works locally is not automatically easy to publish online.

The Lighthouse audit also helped me identify technical weaknesses that were not obvious from using the app manually. The Accessibility score was 80/100, which suggests that the interface has a reasonable foundation but still needs improvement. The audit also showed very low Best Practices and SEO scores. These scores were partly affected by the local prototype context, such as the app being tested through HTTP on localhost and missing production-level metadata. However, they still reveal useful improvement areas: a deployed version should use HTTPS, include a meta description, and handle basic crawlability more carefully. This helped me understand that a working prototype can still be technically incomplete when judged as a deployed web system.

The login system is another example of a useful but limited technical decision. In the final prototype, the demo login supports the intended user flow and allows the app to show a personalised profile state. The user information is stored in localStorage so the interface can remain logged in after refreshing the page. This works well for a prototype, but it is not production-level authentication. A real platform would need password hashing, sessions or tokens, server-side permission checks, and a secure registration process. This evaluation helped me understand the difference between building a feature that demonstrates an interaction and building a feature that would be safe for real users.

From a user experience perspective, EASY DIVE supports the intended users reasonably well. The Log Dive form is structured around diving-specific information, such as current strength, visibility, water temperature, surge condition, common marine life, feeling tags, and personal notes. This makes the app more useful than a general note-taking tool because it guides divers to record information that matters in the diving context. The use of dropdowns and checkboxes also reduces the amount of typing required and makes the data more consistent across records. As shown in Appendix B, a participant familiar with recreational diving was able to understand the purpose of the log form and complete the main tasks, but also found the form visually dense at first.

The Explore Sites page also meets an important user need from the original concept. I wanted users to be able to search and compare dive information contributed by others, not only store their own private logs. The final prototype allows users to filter information by keyword, state, site type, and difficulty. The use of image cards, condition details, short descriptions, and badges makes the information easier to scan. This supports the idea of EASY DIVE as a reference tool for divers who want to decide where to go or what conditions to expect.

The main UX weakness is that the Log Dive page still contains a lot of information at once. Even though the form is organised, it may still feel long or heavy for a first-time user. This reflects a tension in the project: a useful dive log needs enough detail to be meaningful, but too many fields can make the interaction feel demanding. The evidence in Appendix B supports this issue, because the participant could complete the task but still commented that the form looked long at first. If I continued the project, I would redesign the log form into smaller steps, such as Location, Conditions, Marine Life, and Notes. This would make the task feel more manageable while keeping the same data structure.

Accessibility is partly addressed, but it still needs improvement. A positive aspect is that most form inputs have visible labels, which helps users understand what each field is asking for. The visual contrast is generally strong, especially with dark navy text on light backgrounds and white text on dark blue areas. The responsive layout also works well because multi-column layouts become single-column layouts on smaller screens. However, Appendix C shows that the modal profile window is only partly accessible. It has ARIA attributes, but it does not fully manage keyboard focus, and it does not currently support closing with the Escape key. This made me realise that accessibility is not only about readable colours or labelled forms. Interactive components also need to support keyboard users and screen-reader users more carefully.

Looking at the functional requirements, the final prototype met most of the core goals I identified during planning. Users can log in, record a dive, select or enter a dive site, choose environmental conditions, add marine life and feeling tags, view a live preview, save the record, search community dive information, browse local dive shops, and edit profile information. These functions match the main concept of EASY DIVE. The project also includes relationships between users and content, such as displaying who posted a dive site or log. This makes the social aspect more convincing than showing anonymous static content.

At the same time, some original ideas were reduced in scope. The biggest cut was real image upload. In the final prototype, users can paste an image link or use a default image, but they cannot upload a file directly. This was a realistic compromise because real image upload would require backend file handling, storage, validation, and extra security decisions. The social communication feature was also simplified into profile contact links rather than a real messaging or friend system. I think this was the correct decision for the assignment scope. A complete social platform would have been too large, and the final prototype is stronger because it focuses on a smaller number of complete user flows.

One lesson I learned from this project is that functional ambition has to be balanced with implementation clarity. At the start, it was easy to list many possible features because the idea of a diving social platform naturally suggests logging, searching, profiles, shops, images, comments, messaging, and safety information. During development, I had to decide which features were essential for the prototype and which ones could remain future work. The final project became stronger when I focused on complete flows instead of trying to include every possible idea at a shallow level.

I also learned that data structure is a design decision, not only a technical decision. Choosing fields such as visibility, current strength, water temperature, surge, species, and feeling tags shaped the whole user experience. These fields are not just database columns; they define what the app asks users to notice and record. This helped me understand that web development and interaction design are closely connected. The way information is structured in code directly affects what users can do, what they pay attention to, and how useful the final interface becomes.

If I continued developing EASY DIVE, my would be improving deployment and accessibility.  I want to implement a login system that allows real registration or free account login, along with an administrator account to easily delete meaningless records and update dive shop information. It should also support uploading account avatars, allowing users to select images through the system instead of URLs.

---

# Appendix: Evaluation Evidence

The following evidence supports the reflection above. This appendix is separated from the main reflective writing and is not intended to count towards the 1250-word limit.

## Appendix A: Manual Technical Task Walkthrough

| Task tested                                                             | Result | Evidence / observation                                                                                                        | Used in reflection                                                |
| ----------------------------------------------------------------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------- |
| Open the app locally through `npm start` and access `localhost:3000`    | Passed | The app could be opened through the local server after installing dependencies.                                               | Used to discuss local performance and setup complexity.           |
| Log in with the demo account                                            | Passed | The login page accepted the demo username and password and then displayed the main app shell.                                 | Used to discuss prototype-level login and user flow.              |
| Navigate between Home, Log Dive, Explore Sites, Dive Shops, and Profile | Passed | Navigation switched sections without full page reload.                                                                        | Used to evaluate responsiveness and app-like behaviour.           |
| Create a new dive log                                                   | Passed | The form accepted location, conditions, marine life, notes, and image link/default image. After saving, the log list updated. | Used to evaluate functional completion and backend/API behaviour. |
| Use the live preview while filling in the form                          | Passed | The preview changed when fields, checkboxes, notes, or image values changed.                                                  | Used to evaluate immediate feedback and user experience.          |
| Search and filter dive sites                                            | Passed | Keyword, state, site type, and difficulty filters changed the displayed cards.                                                | Used to evaluate client-side filtering and browsing usability.    |
| Edit profile information                                                | Passed | Profile fields could be changed and the profile display updated after saving.                                                 | Used to evaluate profile functionality.                           |

## Appendix B: User Walkthrough

A short walkthrough was conducted with one participant familiar with recreational diving. The participant was asked to complete three core tasks without step-by-step instruction.

| Task                                                | Completion                      | Observation                                                                                                                                                 |
| --------------------------------------------------- | ------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Log in using the demo account                       | Completed                       | The participant understood the demo login because the account details were visible on the login page.                                                       |
| Record and save a new dive log                      | Completed                       | The participant understood the purpose of the fields, especially current, visibility, temperature, and marine life. However, the form looked long at first. |
| Search for a dive site and view related information | Completed                       | The participant found the card layout easy to scan and understood the filter options after trying them.                                                     |
| View a diver profile from a card                    | Completed with minor hesitation | The participant did not immediately realise that the author name was clickable.                                                                             |

Short feedback notes:

> “The live preview makes it easier to understand what I am creating.”

> “The information is useful for divers, but the logging form looks a little long when I first open it.”

> “The site cards are clear because I can see location, type, conditions, and marine life quickly.”

## Appendix C: Accessibility Checklist

| Accessibility area  | Result            | Evidence from prototype                                                                       | Improvement needed                                                                   |
| ------------------- | ----------------- | --------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------ |
| Visible form labels | Mostly passed     | Login, dive log, and profile inputs have visible labels.                                      | Check every field after future layout changes.                                       |
| Colour contrast     | Mostly passed     | Dark navy text on light backgrounds and white text on dark blue areas are generally readable. | Run a formal contrast checker for all button and badge combinations.                 |
| Responsive layout   | Passed            | CSS media queries turn multi-column layouts into single-column layouts on smaller screens.    | Test on more device widths, not only desktop resizing.                               |
| Keyboard navigation | Partly passed     | Standard buttons and form fields are keyboard reachable.                                      | Add stronger visible focus states.                                                   |
| Modal accessibility | Needs improvement | The profile modal has ARIA attributes, but does not fully trap focus or close with Escape.    | Add focus trapping, Escape-key close, and return focus to the clicked author button. |
| Error feedback      | Partly passed     | Login and form errors can be shown as text messages.                                          | Make error messages more specific and ensure screen readers announce them.           |

## Appendix D: Lighthouse Audit Results

The Lighthouse audit was run on the locally served prototype entry page.

| Lighthouse category |         Score | Key issue / observation                                                                                                                                                | Reflection use                                                                                                         |
| ------------------- | ------------: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------- |
| Performance         | Not available | Lighthouse performance trace could not be reliably completed in the local testing environment. Manual task walkthrough was used instead for performance reflection.    | Used to explain why performance was evaluated through local task behaviour rather than a Lighthouse performance score. |
| Accessibility       |      80 / 100 | The site has a reasonable accessibility base, but some accessibility checks still failed or need manual improvement.                                                   | Used to support the accessibility reflection.                                                                          |
| Best Practices      |       0 / 100 | The local prototype was served through HTTP rather than HTTPS. This affected the audit result and shows that deployment-level best practices were not fully addressed. | Used to discuss the difference between a working local prototype and a production-ready deployed system.               |
| SEO                 |       0 / 100 | The page lacks production-level metadata such as a meta description and valid crawlability setup.                                                                      | Used to identify future improvements for public deployment.                                                            |

## Appendix E: Rescoped Functional Requirements

| Original requirement              | Final prototype outcome        | Reflection                                                                                          |
| --------------------------------- | ------------------------------ | --------------------------------------------------------------------------------------------------- |
| User login                        | Implemented as demo login      | Useful for demonstrating the flow, but not secure enough for production.                            |
| Record dive site and conditions   | Implemented                    | Core requirement met through structured fields and database saving.                                 |
| Search community dive information | Implemented                    | Filters and cards support browsing and comparison.                                                  |
| View local dive shops             | Implemented                    | Region-based shop cards support practical local reference.                                          |
| User profile and contact link     | Implemented in simplified form | Supports social identity, but not a full social network.                                            |
| Image upload                      | Rescoped                       | Replaced with image link/default image because real upload was too complex for the prototype scope. |
| Messaging or buddy system         | Rescoped                       | Represented only through contact links; full messaging would require a much larger system.          |

