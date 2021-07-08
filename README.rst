Quart-SQLAlchemy
================

**WARNING**

- This extension is work-in-progress and is for internal use (for now).
- It works with raw queries and is tested only on asyncpg.
- Base class implements convenience method inspired by encode/databases.
- Documentation and tests TODO.

---

Quart-SQLAlchemy is an extension for `Quart`_ that adds support for
`SQLAlchemy`_ to your application. It aims to simplify using SQLAlchemy
with Quart by providing useful defaults and extra helpers that make it
easier to accomplish common tasks.

.. _Quart: https://palletsprojects.com/p/quart/
.. _SQLAlchemy: https://www.sqlalchemy.org


Installing
----------

Install and update using `pip`_:

.. code-block:: text

  $ pip install -U Quart-SQLAlchemy

.. _pip: https://pip.pypa.io/en/stable/quickstart/


A Simple Example
----------------

.. code-block:: python

    from quart import Quart
    from quart_sqlalchemy import SQLAlchemy

    app = Quart(__name__)
    app.config["SQLALCHEMY_DATABASE_URI"] = "sqlite:///example.sqlite"
    db = SQLAlchemy(app)


    class User(db.Model):
        id = db.Column(db.Integer, primary_key=True)
        username = db.Column(db.String, unique=True, nullable=False)
        email = db.Column(db.String, unique=True, nullable=False)


    db.session.add(User(username="Quart", email="example@example.com"))
    db.session.commit()

    users = User.query.all()


Contributing
------------

For guidance on setting up a development environment and how to make a
contribution to Quart-SQLAlchemy, see the `contributing guidelines`_.

.. _contributing guidelines: https://github.com/pallets/quart-sqlalchemy/blob/master/CONTRIBUTING.rst


Donate
------

The Pallets organization develops and supports Quart-SQLAlchemy and
other popular packages. In order to grow the community of contributors
and users, and allow the maintainers to devote more time to the
projects, `please donate today`_.

.. _please donate today: https://palletsprojects.com/donate


Links
-----

-   Documentation: https://quart-sqlalchemy.palletsprojects.com/
-   Changes: https://quart-sqlalchemy.palletsprojects.com/changes/
-   PyPI Releases: https://pypi.org/project/Quart-SQLAlchemy/
-   Source Code: https://github.com/pallets/quart-sqlalchemy/
-   Issue Tracker: https://github.com/pallets/quart-sqlalchemy/issues/
-   Website: https://palletsprojects.com/
-   Twitter: https://twitter.com/PalletsTeam
-   Chat: https://discord.gg/pallets
