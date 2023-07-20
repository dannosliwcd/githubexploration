README
------

Here is a simple flow chart:

.. code:: mermaid
  
  flowchart TD
    submit["User submits job"]
    queuejob["<b>queuejob hook</b>
      Set job's power to minimum power that meets slowdown requirements"]
    start["Job Starts"]
    prologue["<b>execjob_prologue hook</b>
      Save current node power limits and set new limits equal to the job's allocated power per node"]
    finish["Job Finishes"]
    epilogue["<b>execjob_epilogue hook</b>
      Restore saved power limits."]

    submit:::event-->queuejob:::hook-->start:::event-->prologue:::hook-->finish:::event-->epilogue:::hook
    classDef event fill:#dde9af
    classDef hook fill:#4472c4,color:#fff
