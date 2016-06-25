# LOA

> *LOA: a digital assistant for the 21st century*

LOA is a **L**ife **O**rganizer **A**pp that aggregates together a variety of social media apps, note-taking apps, productivity apps, communication apps, calendar apps, etc. that you already use to help manage your digital life.

It's great that all of these apps exist, but what's not so great is the feeling that you have to continually keep yourself up-to-date with all of their separate feeds and remember to use all of them. LOA combines all of your feeds, calendars, contacts, etc. into a single, easy-to-use application.

## Dependencies

- java 1.7+
- [boot][1]

## Usage

### Development
1. Start the `dev` task. In a terminal run:
    ```bash
    $ boot dev
    ```
    This will give you a  Hoplon development setup with:
    - auto compilation on file changes
    - audible warning for compilation success or failures
    - auto reload the html page on changes
    - Clojurescript REPL

2. Go to [http://localhost:8000][2] in your browser. You should see "Hello, Hoplon!".

3. If you edit and save a file, the task will recompile the code and reload the
   browser to show the updated version.

### Production
1. Run the `prod` task. In a terminal run:
    ```bash
    $ boot prod
    ```

2. The compiled files will be on the `target/` directory. This will use
   advanced compilation and prerender the html.

## License

Copyright © 2016 Dave Yarwood

Distributed under the Eclipse Public License version 1.0.

[1]: http://boot-clj.com
[2]: http://localhost:8000
