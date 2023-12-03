
Apache Airflow is an open-source workflow orchestration platform, developed with [[Python]] and utilizing the [[Flask]] framework for the web server component. It is created by the [[Apache Software Foundation]] and designed to programmatically author, schedule, and monitor workflows, which are defined as DAGs (Directed Acyclic Graphs).

## Starting Apache Airflow easily using [[Docker]]

You can directly install Apache Airflow with PyPi if you are using macOS or Linux. However with [[Docker]] or [[Helm Chart]], there's nothing to waste time setting up dependency libraries or other environments.

## Operator

Operator is a component of DAGs, pre-defined & templated task. It can be defined declaratively inside the DAG. This contains the logic for how data is processed in the pipeline.

``` python
# DOCS -> https://airflow.apache.org/docs/apache-airflow/stable/howto/custom-operator.html
# BaseOperator -> # https://airflow.apache.org/docs/apache-airflow/stable/_api/airflow/models/baseoperator/index.html#airflow.models.baseoperator.BaseOperator

from typing import *

from airflow.models.baseoperator import BaseOperator
from airflow.utils.decorators import apply_defaults
from airflow.utils.context import Context


class MyCustomOperator(BaseOperator):


    # To use Jinja template, consider the field names present in the template_fields attribute.
    template_fields: Sequence[str] = ("param_name", )
    template_ext: Optional[str] = ".sql" # If the parameter contains file name, set the file extension here.
    template_fields_renderers: Optional[dict] = {
        "param_name": "py",
        "another_param": "json"
    } # This defines in what style the value from template field renders in Web UI

    @apply_defaults
    def __init__(
            self,
            param : str,
    ) -> None
        
        """
        Description
        
        :param param: parameter description
        :returns: None
        :raises AssertionError: if param is not an str
        """

        super().__init__()
        
        self.param = param
        
        assert isinstance(self.param, str), f"param is not str, it is {type(self.param).__name__}."

    # This function is called ahead of execute() function.
    def pre_execute(self, context: Context) -> None:

        # Statements here
        super().pre_execute() # Optional

    # Defines the operator's actual work.
    def execute(self, context: Context) -> None:

        # Statements here
        super().execute(context) # If you want to execute the parent class's execute method, call it explicitly.

    # This function is called when the task instance is killed.
    def on_kill(self) -> None:

        # Statements here
        super().on_kill() # Optional
```

### Competitors or alternatives

1. **[[Apache Oozie]]** by [[Apache Software Foundation]]
2. **[[Amazon Managed Workflows for Apache Airflow (MWAA)]]** by [[AWS (Amazon Web Services)]]
3. **[[AWS Step Functions]]**
4. **[[Cloud Composer]]** by **[[Google Cloud Platform (GCP)]]**
5. **[[Prefect]]**