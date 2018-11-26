# Node 

<details>
<summary>What is Node?</summary>
  
Node (more formally _Node.js_) is a runtime executed as a process on your computer which can run JavaScript code.

After downloading it from [its homepage](https://nodejs.org/en/) or better installing it through [your operating systems package manager](https://nodejs.org/en/download/package-manager/) (e.g. on Ubuntu `curl -sL https://deb.nodesource.com/setup_11.x | sudo -E bash -; sudo apt-get install -y nodejs`) you then have a program called `node` which you can invoke from the command line:

    node -e 'console.log(Math.random())'

will print a random float on the console.

You can also execute a JavaScript file like this:

    echo 'console.log(Math.random())' > random.js
    node random.js

_Node.js_ is similar to the JavaScript engine in your browers in the sense that it understands the same language. But when it comes to writing software with it, it is very different. You will very quickly encounter a package manager like [npm](https://docs.npmjs.com/about-npm/) to pull in libraries which you need for your project. These dependencies are managed through a file called [`package.json`](https://flaviocopes.com/package-json/) which you will find in basically every Node.js project folder.

</details>

----

<details>
<summary>Do I need to learn Express?</summary>
  
If you know the answer to this question, please submit a pull request with the answer.

</details>

_Waiting for response_


----

<details>
<summary>Does Node replace Java or Python?</summary>
  
If you know the answer to this question, please submit a pull request with the answer.

</details>

_Waiting for response_
