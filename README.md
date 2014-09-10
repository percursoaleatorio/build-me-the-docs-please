Project Management Tools
========================

This is a public `git` repository for documentation about 
various project management tools and related software.
It basically contains information for users, tips, tricks and small how-to-do descriptions.

How to use the repository:
---------------------------

1. Create an account in Github.
2. Fork the `master` repository.

3. Install `git` on your computer.
4. Create a local repository (by cloning your fork).
5. Create a branch to store your work (e.g. `myChangesToRequirements`).
5. Make changes, local commits, etc..
6. Commit to your fork.
7. When you want your changes to be reviewed 
   and integrated into the `master`, send a `pull request`.

8. Your changes will be reviewed and merged into the main branch.
9. Update your repositories to avoid conflicts.
   
Please read `/docs/build/html/On_VersionControl/UsingGit.rst`

Documents are stored in:
-------------------------

Textual information is stored in reStructured Text files (`rst` files).
Please read `/docs/build/html/On_Documentation/OnReStructuredText.rst`

Images are stored in `png` format.

The documents are stored in:

*  the `/docs/source/` folders.

Please do not change:

*  the `.gitignore` file
*  the `/docs/makefile` and the `mosy/docs/make.bat` file (required by Sphinx)
*  the `/docs/source/conf.py` file (required by Sphinx)
*  the `/docs/_static` directory 
*  the `/docs/_templates` directory 
*  the `/docs/_themes` directory 
*  the `/utils` directory content

Each subdirectory (may) contain:

*  an `index.rst` file with the partial table of contents of the directory

*  a `Z_GenericLinks.rst` file with all the hyperlinks required by the documents 
   in the directory. 
   An ``..include::`` directive is used to include the file at the end 
   of ther refereing documents (after the ``.. links-placeholder``.
   
*  a `Z_References.rst` file containing bibliographic references. 
   Later on, this files will be consolidated into a bibtex file,
   and all citations will be changed accordingly.
   
*  an `img` directory containing images used in the documents. 

Documents are built with Sphinx.
---------------------------------

