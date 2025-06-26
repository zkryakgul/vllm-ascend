# Additional Configuration

addintional configuration is a mechanism provided by vLLM to allow plugins to control inner behavior by their own. vLLM Ascend uses this mechanism to make the project more flexible.

## How to use

With either online mode or offline mode, users can use additional configuration. Take Qwen3 as an example:

**Online mode**:

```bash
vllm serve Qwen/Qwen3-8B --additional-config='{"config_key":"config_value"}'
```

**Offline mode**:

```python
from vllm import LLM

LLM(model="Qwen/Qwen3-8B", additional_config={"config_key":"config_value"})
```

### Configuration options

The following table lists the additional configuration options available in vLLM Ascend:

| Name                          | Type | Default | Description                                                                                   |
|-------------------------------| ---- |------|-----------------------------------------------------------------------------------------------|
| `torchair_graph_config`       | dict | `{}` | The config options for torchair graph mode                                                    |
| `ascend_scheduler_config`     | dict | `{}` | The config options for ascend scheduler                                                       |
| `expert_tensor_parallel_size` | str  | `0`  | Expert tensor parallel size the model to use.                                                 |
| `refresh`                     | bool | `false` | Whether to refresh global ascend config content. This value is usually used by rlhf or ut/e2e test case.     |
| `expert_map_path`             | str  | `None` | When using expert load balancing for the MOE model, an expert map path needs to be passed in. |
| `chunked_prefill_for_mla`     | bool | `False` | Whether to enable the fused operator-like chunked_prefill. |

The details of each config option are as follows:

**torchair_graph_config**

| Name | Type | Default | Description |
| ---- | ---- | ------- | ----------- |
| `enabled` | bool | `False` | Whether to enable torchair graph mode |
| `enable_multistream_mla`| bool | `False` | Whether to put vector ops of MLA to another stream |
| `enable_multistream_moe`| bool | `False` | Whether to enable multistream shared expert |
| `enable_view_optimize` | bool | `True` | Whether to enable torchair view optimization |
| `use_cached_graph` | bool | `False` | Whether to use cached graph |
| `graph_batch_sizes` | list[int] | `[]` | The batch size for torchair graph cache |
| `graph_batch_sizes_init` | bool | `False` | Init graph batch size dynamically if `graph_batch_sizes` is empty |
| `enable_kv_nz`| bool | `False` | Whether to enable kvcache NZ layout |

**ascend_scheduler_config**

| Name | Type | Default | Description |
| ---- | ---- | ------- | ----------- |
| `enabled` | bool | `False` | Whether to enable ascend scheduler for V1 engine|

ascend_scheduler_config also support the options from [vllm scheduler config](https://docs.vllm.ai/en/stable/api/vllm/config.html#vllm.config.SchedulerConfig). For example, you can add `enable_chunked_prefill: True` to ascend_scheduler_config as well.

### Example

An example of additional configuration is as follows:

```
{
    "torchair_graph_config": {
        "enabled": True,
        "use_cached_graph": True,
        "graph_batch_sizes": [1, 2, 4, 8],
        "graph_batch_sizes_init": False,
        "enable_multistream_moe": False,
        "enable_kv_nz": False
    },
    "ascend_scheduler_config": {
        "enabled": True,
        "enable_chunked_prefill": True,
    },
    "expert_tensor_parallel_size": 1,
    "refresh": False,
}
```
