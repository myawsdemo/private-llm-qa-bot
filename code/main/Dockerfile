FROM --platform=linux/amd64 public.ecr.aws/lambda/python:3.9

COPY requirements.txt  .

RUN  pip3 install -r requirements.txt --target "${LAMBDA_TASK_ROOT}"

# Copy function code
COPY main.py ${LAMBDA_TASK_ROOT}
COPY utils ${LAMBDA_TASK_ROOT}/utils
RUN mkdir -p ${LAMBDA_TASK_ROOT}/generator
RUN mkdir -p ${LAMBDA_TASK_ROOT}/retriever
COPY generator/*.py ${LAMBDA_TASK_ROOT}/generator/
COPY retriever/*.py ${LAMBDA_TASK_ROOT}/retriever/

# Set the CMD to your handler (could also be done as a parameter override outside of the Dockerfile)
CMD [ "main.lambda_handler" ]