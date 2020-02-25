# 👋💻😅 Welcome to Automattic‘s Coding Test
The interview was fun, right? We’re excited to welcome you to the next stage – you earned it. Now it’s time to get started writing some code.

## 🐕 The Rusty Inc. Org Chart WordPress Plugin

Rusty Inc. is the leading corporation offering free benefits to both canine and human societies.

To improve their internal website, you will help them with the organizational chart editor and viewer. It’s implemented as a WordPress plugin. Activate the plugin and you will see a “Rusty Inc. Org Chart” item almost at the top of the menu.

Right now some of the functionality is missing and we need your help! Below are your tasks, **please answer any questions asked in GitHub issues.**

## 🤹 Your Tasks
* Make the buttons work: When you visit the “Rusty Inc. Org Chart” page, there are ➕ and 🚫 buttons. Please make these functional. Feel free to use `askUserForTeamDetails` and `askUserForDeleteConfirmation` functions in `ui.js`. No need to implement the server-side “✅ Save” functionality, you can assume it will get done.
* Hide the URL and Save parts of the tree when viewed as a shared page.
* Make the collapse animation faster and use computer resources more effectively: The expand/collapse animation is supposed to take 1500ms, but it’s much slower and there's noticeable CPU load. On a newer browser you can see the actual animation duration in the console.  Please, also add a short note on GitHub detailing how would you explain to the colleague who wrote this code why the animation was so slow.
* Perform a security audit on both the front-end and the backend of the plugin. Please, also add a short note on GitHub about how exactly would an attacker exploit each security problem that you found. Finding the security problems is a crucial part of this test, so it deserves a small hint – in the code you will find few classic OWASP Top 10 vulnerabilities, a logic error, and a problem only relevant if the plugin was to be released and installed on several sites. None of them are WordPress or PHP-specific.
* Please make sure to accompany your code changes with some automated tests, where you find necessary. While tests will not detect all problems, they can help point out the obvious ones.
* Answer this question as an open issue in your GitHub repo: how many different secret keys can be generated with the current approach using `wp_generate_password`?
* Answer this question as an open issue in your GitHub repo: what in the plugin's front-end architecture would you change? Why? Since architecture is a very broad term, please consider high-level design decisions about the performance of the plugin, how easy it is to change, its security, and its extensibility.
* To keep things simpler, a couple of limitations:
	- the plugin shouldn’t include any dependencies from `npm` and also shouldn’t need a build process. Development dependencies like linters, `prettier` or the like are OK, if they make your life easier;
	- DOM manipulation should be limited to the framework level (`framework.js`) and ideally the UI level should contain only declarations of DOM structure.

## ⏳ Time
* We ask that you spend **6 hours total** on this test (not counting any needed research time) and that you complete it within **one week** of the test being sent to you. To be clear, please do not spend a full week of work on this and do not spend more than 6 hours. We don't want to take up too much of your time. If you find the test is taking more than the expected 6 hours, we've got some [additional tips in the FAQ](#its-taking-me-more-than-the-suggested-5-6-hours-what-should-i-do)
* As a tip, we recommend planning out your time to focus on different tasks before starting and adopt a “timeboxing” approach. To explain, timeboxing is the idea that instead of working on a task until it’s done, you commit to work on it for a specific amount of time instead. This should result in better focus, more free time for you, less opportunities for the plugin to become complex, and easier to avoid the inevitable rewrite-from-scratch tendencies (please, don't rewrite the whole plugin).
* When done, please ping us on Slack in the shared group channel. From there, we will organize a member of our team to review your work. 
* We understand that life happens! If you need more than a week to complete the test, don't worry, just ping us in Slack. 

## 🎹 Development
👷 Everything should be already be set up for you! We're experimenting with a zero-setup cloud based editing environment using VSCode, to avoid lengthy setup issues and to get you started straight away. We recommend using Chrome-based browsers, as Microsoft are still working out some kinks in other browsers.

* Visit [https://alisonwonderlandapps.vscode.devex.live](https://alisonwonderlandapps.vscode.devex.live) to access our cloud-based editor, use the password `388b14de6d908944930015308a46c4ed` to login, then wait until this `README.md` loads before you get started!
* Your WordPress development site is available at [https://alisonwonderlandapps.wp.devex.live](https://alisonwonderlandapps.wp.devex.live). Use your `alisonwonderlandapps` as the username, and `388b14de6d908944930015308a46c4ed` as the password.
* Here's a link to the plugin page for your convenience: [https://alisonwonderlandapps.wp.devex.live/wp-admin/admin.php?page=rusty-inc-org-chart](https://alisonwonderlandapps.wp.devex.live/wp-admin/admin.php?page=rusty-inc-org-chart)
* You have access to a `bash` terminal within VSCode, via the hamburger menu's Terminal item.
* You will need to use `git` for source control, please ensure you're familiar [with the basics](https://guides.github.com/introduction/git-handbook/) before starting out. 
* When `git push`ing via the terminal, you'll need to enter a Personal Access Token as your password for GitHub. Please create one here, and keep it safe: [https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line)

### ⏸ Debugging PHP with XDebug

* Simply click the debugging icon on the VSCode sidebar, and you can start XDebug by clicking "Play" for the "Listen for XDebug" configuration. You will be able to add breakpoints on specific lines in the editor, and view the callstack etc.

### ⏱ Profiling PHP with XDebug

* Append `XDEBUG_PROFILE` param to either GET or POST parameters. The profiler will write to the `.cachegrind` folder, and you should download the files it outputs locally, using `kcachegrind`, or`qcachegrind` etc to open them. The URL will be `https://alisonwonderlandapps.wp.devex.live/wp-content/plugins/rusty-inc-org-chart/.cachegrind/<file>`

### 👉 Process
* The final deliverable should be _one_ [pull request](https://help.github.com/articles/creating-a-pull-request/) in the repository. 
* If it will help you, feel free to use the GitHub issues or project functionality, though it's not mandatory at all.
* If you have any questions, let us know, we'd be happy to be your both product and technical partner.

### 💉 Running tests:

* For the PHP tests,  run `phpunit` from your terminal in VSCode.
* For the JavaScript tests, visit [https://alisonwonderlandapps.wp.devex.live/wp-content/plugins/rusty-inc-org-chart/tests/test.html](https://alisonwonderlandapps.wp.devex.live/wp-content/plugins/rusty-inc-org-chart/tests/test.html)

### 💡 Helpful tips:

* Back-end entry point: have a look at `class-rusty-inc-org-chart-plugin.php` and the `add_init_action`.
* Front-end entry point: the bootstrap code is in `admin-page-inline-script.php`. Hydrating the UI is much easier through an inline script than via AJAX calls.

## ✅ What To Pay Attention To Besides The Tasks
* Simplicity – we would consider it a win if the code does not get more complex after adding more features and fixing issues.
* Make the changes easy to review – detailed pull request descriptions, small pull requests, commit granularity, descriptive commit messages.
* Design and code quality — separation of concerns, abstraction, naming…
* Backwards compatibility – if you make changes to how the plugin works, make sure users who have already installed it won’t have trouble upgrading.
* Browser compatibility – the plugin should work well under Edge 16+, Firefox 60+, Chrome 67+, Safari 11+.

## 😐 What To Not Pay Too Much Attention To
These are still important, but we thought for this test they would be a distraction:

* WordPress or PHP internals – the language should have familiar enough syntax and we have tried to put some extra pointers about how WordPress works. Ideally you shouldn't need more than a quick Google search to accomplish what you need. **This is not a test for your PHP or WordPress skills.**
* PHP minimum version – WordPress core still works on PHP 5.2 (ancient). On WordPress.com we run the latest PHP version, so no need to worry about that.
* Internationalization – normally a very important part of the development process, because it allows people from all over the world to use our software. However, in this case, it would add too much complexity, so we decided to omit it for now.
* Asset size and number of HTTP requests – another usually important consideration that we can forgo for now, because the plugin will be used in an intranet and under HTTP/2.

## 🙋 Frequently Asked Questions

### I found a problem. Is fixing it part of the task?
It depends on the severity of the problem and the available time. This will be a great case for your prioritization skills to shine :) Please, note all problems, order them by their priority, fix the top ones if you have some time left, and show us the prioritized list of the ones that still need fixing.

### I am working on the front-end, but part of the task (security, number of keys) requires work on the back-end. Is that intentional?
Yes. Being able to read both back-end and front-end code and implement simple changes is important, even if it's not your main focus.

### It’s taking me more than the suggested 5-6 hours, what should I do?
It depends on why is it taking longer. Few tips:

* Avoid spending too much time on any one task and getting lost in the details – if you are stuck with something, feel free to ask us for help, whether it’s a configuration issue, a problem to debug, or another way to unblock you, we’ll be happy to help.
* Prioritize – make sure you do the most important tasks first and leave the “nice to haves” for if you have enough time.
* “The technologies are too foreign” – we have assumed familiarity with: how a web server side works, a C-based server-side language, and some browser and JavaScript knowledge. We have left some comments to guide you through the WordPress-specific bits, but by all means, if you can't find an answer to your question with a quick Google search, ask us. The goal is not to test the knowledge about a specific language or framework.
