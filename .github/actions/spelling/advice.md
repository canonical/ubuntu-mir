<!-- See https://github.com/check-spelling/check-spelling/wiki/Configuration-Examples%3A-advice --> <!-- markdownlint-disable MD033 MD041 -->
<details>
<summary>
:pencil2: Contributor please read this
</summary>
By default the suggested command will add the listed items to the <code>.github/actions/spelling/expect.txt</code>. <b>This is not allways desired!</b>

If a listed items is
* ... **misspelled**, then please *correct* them instead of changing the spell checker configuration.
* ... an *actual* word/term that has a high probability of showing up in future contributions, please add it to the [`allowed words`](/.github/actions/spelling/allow).
* ... an term/word that just you use or shouldn't generally be accepted, please add it to [`.github/actions/spelling/expect.txt`](/.github/actions/spelling/expect.txt).

See the `README.md` in each directory for more information.

:microscope: You can test your commits **without** *appending* to a PR by creating a new branch with that extra change and pushing it to your fork. The [check-spelling](https://github.com/marketplace/actions/check-spelling) action will run in response to your **push** – it doesn't require an open pull request. By using such a branch, you can limit the number of typos your peers see you make. :wink:

</details>
