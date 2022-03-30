FROM tensorflow/tensorflow:2.8.0-gpu

RUN pip install dash matplotlib numpy>=1.9 pandas>=1.1 \
                scikit-learn scipy>=0.14 tensorflow-probability

RUN curl https://codeload.github.com/coryshain/cdr/zip/refs/heads/dev -o dev.zip \
                    && unzip -q dev.zip && rm dev.zip \
                    && mv cdr-dev /opt/cdr
ENV PYTHONPATH=/opt/cdr:$PYTHONPATH
