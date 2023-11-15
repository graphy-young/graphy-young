
Workflow Orchestration Platform, made by [[Apache Software Foundation]].
Based on [[Python]] [[Flask]] [[framework]], 

## Custom Operator
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

### Competitors
1. **[[Apache Oozie]]**
2. **[[Amazon Managed Workflows for Apache Airflow (MWAA)]]**
3. **[[AWS Step Functions]]**
4. **[[Google Cloud Platform (GCP)]]** **[[Cloud Composer]]**
5. **[[Prefect]]**