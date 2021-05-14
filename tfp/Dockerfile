FROM tensorflow/tensorflow:2.5.0rc1-gpu-jupyter

RUN pip install "git+https://github.com/google/edward2.git#egg=edward2" && \
pip install --upgrade tensorflow-probability numpy scipy pandas arviz seaborn pyarrow
