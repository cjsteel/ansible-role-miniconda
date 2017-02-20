# file: roles/miniconda/ROADMAP.md

## variable expansions when/if required

Example:

miniconda_envs:
  name: ansible-1.9
  channels:
    - csteel
  dependencies:
    - ansible=1.9
    - python=2.7
    - bokeh=0.9.2
    - numpy=1.9.*
    - nodejs=0.10.*
    - pip:
      - ipython
  name: ansible-2.0.5
  channels:
    - csteel   
  dependencies:
    - ansible=2.0.5
    - python=2.7 
    - bokeh=0.9.2
    - numpy=1.9.*
    - nodejs=0.10.*
    - pip:

