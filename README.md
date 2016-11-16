
1. Clone o repositório:
   ```
   git clone <git repo name>
Example:
   git clone https://github.com/Microsoft/EMDocs-pr.git
   ```

2. Exemplo:
   git clone https://github.com/Microsoft/EMDocs-pr.git
3. git add -u
   git commit -m "update doc"
   git push
4. Validate and preview your content locally, to discover and fix problems early, before pushing your changes to the GitHub repo:
   * Run <ph id="ph1">`git submodule update --init`</ph> to download the themes to your local machine.
   * Follow the instructions in <bpt id="p1">[</bpt>Local builds and preview page<ept id="p1">](https://ppe.msdn.microsoft.com/en-us/openpublishing/docs/partnerdocs/local-build-and-preview)</ept>
5. Commit and push your changes:
   ```
   git add -u
   git commit -m "update doc"
   git push
   ```
6. Create a pull request to master branch.
7. Your content will be automatically published once the pull request is accepted.




