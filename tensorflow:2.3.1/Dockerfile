From tensorflow/tensorflow:2.3.1-jupyter
LABEL maintainer="theabc50111@gmail.com"

RUN pip3 install jupyterthemes pandas scikit-learn; \
jt -t onedork -T -N -kl -fs 16 -tfs 16 -ofs 14 \
-mathfs 100 -dfs 14 -nfs 14 -cellw 90% -lineh 170; \
rm -rf /tf/tensorflow-tutorials; \
mkdir -p /root/.jupyter/nbconfig; \
touch /root/.jupyter/nbconfig/notebook.json; \
echo '{\
\n  "MarkdownCell": {\
\n    "cm_config": {\
\n      "lineWrapping": true\
\n    }\
\n  },\
\n  "CodeCell": {\
\n    "cm_config": {\
\n      "lineWrapping": true\
\n    }\
\n  }\
\n}'>/root/.jupyter/nbconfig/notebook.json; \
mkdir -p /root/.ipython/profile_default/startup; \
touch /root/.ipython/profile_default/startup/startup.ipy; \
echo "# use ggplot as style of picture\
\nimport matplotlib.pyplot as plt\
\nplt.style.use('ggplot')">/root/.ipython/profile_default/startup/startup.ipy; \
jupyter notebook --generate-config; \
echo "c.NotebookApp.ip = '*'\
\nc.NotebookApp.open_browser = False\
\nc.NotebookApp.allow_root = True">>/root/.jupyter/jupyter_notebook_config.py; \
mkdir -p $(jupyter --data-dir)/nbextensions; \
cd $(jupyter --data-dir)/nbextensions; \
git clone https://github.com/lambdalisue/jupyter-vim-binding vim_binding; \
jupyter nbextension enable vim_binding/vim_binding

CMD jupyter notebook
