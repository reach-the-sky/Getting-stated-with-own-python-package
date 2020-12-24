# Getting Started With Making Your Own Python Package

The Python Package Index (PyPI) is a repository of software for the Python programming language.
So all python packages are stored in PyPi

__Create the files in the following order__
> packaging_tutorial <br/>
&nbsp; |--- LICENSE <br/>
&nbsp; |--- README.md <br/>
> &nbsp;     |--- example_pkg <br/>
> &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;   &nbsp; &nbsp;       |---    \__init__.py <br/>
> &nbsp; |--- setup.py <br/>
> &nbsp; |--- tests <br/>


Write yout functions in the \__init__.py file.

Example:
```python
def name():
    print("My name is "......" ")
```

&nbsp;
Open setup.py and paste the code. ( variables with ###...### need to be changed ) (`Enter a Unique Package name`)

```python
import setuptools

with open("README.md", "r", encoding="utf-8") as fh:
    long_description = fh.read()

setuptools.setup(
    name=" example-pkg-(### Package Name ###) ", # Replace with your own username
    version="0.0.1",
    author=" (###Your name###) ",
    author_email=" (###Your email###) ",
    description=" (###Description about your package###) ",
    long_description=long_description,
    long_description_content_type="text/markdown",
    url="https://github.com/pypa/sampleproject",
    packages=setuptools.find_packages(),
    classifiers=[
        "Programming Language :: Python :: 3",
        "License :: OSI Approved :: MIT License",
        "Operating System :: OS Independent",
    ],
    python_requires='>=3.6',
)
```
&nbsp;
Put description about your file in README.md file (using Markdown)

```markdown
# Example Package
This is a simple example package.
```

Creating LICENSE. &nbsp; (Replace [year] \[fulname] with your details ).

```text
MIT License

Copyright (c) [year] [fullname]

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
&nbsp;
Open `cmd` in __packaging_tutorial__ folder and run the commands.

>`py -m pip install --user --upgrade setuptools wheel`

>`py setup.py sdist bdist_wheel`


&nbsp;
The following files will be created after runnimg the commands.
>dist
> &nbsp;  &nbsp; |---example_pkg_YOUR_USERNAME_HERE-0.0.1-py3-none-any.whl
> &nbsp; &nbsp; |---example_pkg_YOUR_USERNAME_HERE-0.0.1.tar.gz


### Uploading the Packages 
First create an account at [Pypi](https://test.pypi.org/account/register/).

Now create a PyPl [API token](https://test.pypi.org/help/#apitoken).
Open command prompt from folder packaging_tutorial and execute these commands.
&nbsp;
>`py -m pip install --user --upgrade twine`

>`python3 -m twine upload --repository testpypi dist/*`

Enter your username and password to upload the package.


### You uploaded your package😀.

After uploading you can look at your repository at [https://test.pypi.org/project/Your package name](https://test.pypi.org/project/example-pkg-YOUR-USERNAME-HERE)

Download in cmd

>python3 -m pip install --index-url https://test.pypi.org/simple/ --no-deps example-pkg-YOUR-USERNAME-HERE

&nbsp;
Now you can open python
>import example_pkg

