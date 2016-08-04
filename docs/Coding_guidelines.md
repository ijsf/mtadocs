Introduction
============

So you've decided to become a contributor to our project. Excellent! But before we can start accepting your code, there are a couple of things you should know about how we work. These are mostly guidelines and rules as to how your code should be structured and how it can be committed without upsetting any fellow contributors.

Code repository
===============

Structure
---------

Our code repository uses Git and is structured into number of different directories, which serve different purposes:

-   **.github**: markdown files only used by the GitHub interface
-   **MTA10**: MTA client code
-   **MTA10\_Server**: MTA server code
-   **Shared**: MTA client & server code
-   **irc**: bot code for the Multi Theft Auto IRC channels
-   **m4**
-   **utils**: utilities used to automate certain tasks
-   **vendor**: unmodified third-party code and libraries (optionally linked to the appropriate third-party Git repository through Git submodules).

Our branches contain groundbreaking research, radical ideas and other work-in-progress that is meant to be merged into the trunk at a later point, but also contains project milestones:

-   The master branch is the main development branch (containing the latest, bleeding-edge code)
-   Project milestones are kept away from the trunk for stability reasons, but the latest version branch can be used by any regular player who has enabled nightly builds. Make sure that only well tested code is added to the latest version branch.

Gaining and Losing Commit access
--------------------------------

Commit access is granted after patches have been submitted, and the coder has proven to be competent. The subject matter of the patches does not matter, we are more interested in whether if you are granted commit access, you will be capable of maintaining a high standard of code and remaining cohesive with other project contributors.

Patches can be submitted using [GitHub's pull request system](https://github.com/multitheftauto/mtasa-blue/pull/new). Usually commit access is gained after 2-3 patches, but this is not fixed and depends on the extent of the contributions. This requires you to fork our repository and make commits to your own branch first.

After gaining commit access, if the contributor's commits are of a consistently low standard, or the user fails to stick to the rules, their commit access will be stripped and will be required to submit pull requests again.

Committing code
---------------

Keep in mind that your commits should initially be fixing or implementing existing issues on our [bug tracker](http://bugs.mtasa.com). The [roadmap](http://bugs.mtasa.com/roadmap_page.php) is particularly important since it allows contributors to track down priority issues.

Please follow these guidelines for all your contributions:

-   Commits should be thoroughly tested when added to master. Commits that 'need to be fixed later' which directly affect the state of the mod will be reverted other than in exceptional circumstances.
-   If writing unstable or experimental code, a private branch should be added in your own fork. Branches should not be “personal” to each user. This means that a branch should be created for a new feature, not for a user specific playground.
-   Commit messages should always give a clear indication of the content of the change, without having to look at the code at all. Where appropriate, include the Mantis Issue number in your log message and keep your log messages consistent, e.g. **Fix \#1234: description and notes here**. [Follow the seven rules identified here.](http://chris.beams.io/posts/git-commit/)
-   When committing updates to previous commits, include the previous commit SHA (and a summarised commit message) in the new commit message. Doing this will help identify related commits if they are viewed at a later date.

Ratings and comments
--------------------

Ratings and comments are open for the public to review code and provide feedback. Please be mature and civilised when posting comments. Developers should try to review other contributor's commits and provide feedback as much as possible.

Make sure you make appropriate use of the GitHub Reactions feature to rate commits or express agreement/disagreement to a comment. This avoids spammy comments such as "+1", "-1", “Nice one!”, etc.

Since you can only react to comments, not commits, feel free to create the initial "+1" comment in response to a commit. However, future reactions to a commit should be to the first response comment.

What to code
------------

Generally, developers should try to stick to the [roadmap](http://bugs.mtasa.com/roadmap_page.php) when coding. This lists the issues required to be resolved for the next release. Of course, if you're interested in something else, feel free to experiment and submit it.

Style
-----

-   We use 4 spaces instead of tabs.
-   Hungarian notation for variable names.

`float         fValue;               // Local variable`
`unsigned char m_ucValue;            // Class member variable`
`char          ms_cValue;            // Class static variable`
`bool          g_bCrashTwiceAnHour;  // Global variable`
`char*         szUsername;           // Zero terminated string`
`SString       strUsername;          // String`
`CVector       vecPosition;          // 3D Vector`

-   Lower camel case for variable names of types like custom structs and enums:

`SSomeStruct   valueOne;`
`ESomeEnum     m_valueTwo;`

-   Function names use UpperCamelCase:

`void UpperCamelCase( void )`

-   A space between almost everything:

`int iResult = 2 + 4 * GetValue() + 123;`

-   A space between a function name and the open parenthesis is optional:

`void OkOne ( void )`
`void OkTwo( void )`
`OkThree ();`
`OkFour();`

-   Functions with no arguments are declared and defined with ( void ), and called with ()

`void MyTest( void );`
`void MyTest( void ) { return; }`
`MyTest();`

-   Functions and member variables of classes/structs are all lined up in neat columns:

`void       FunctionOne     ( void );`
`void       FunctionTwo     ( void );`
`float      fValue;`

-   For anything else, follow the style of the code that already exists.

[Category: Development](/Category:_Development.md "wikilink")
