
- babyagi
	- [chart of mvp](https://dreampuf.github.io/GraphvizOnline/#digraph%20G%20%7B%0A%20%20%20%20label%20%3D%20%22AI%20Task%20Management%20Workflow%22%3B%0A%20%20%20%20compound%3Dtrue%3B%0A%0A%20%20%20%20subgraph%20cluster_init%20%7B%0A%20%20%20%20%20%20%20%20label%20%3D%20%22Initialize%22%3B%0A%20%20%20%20%20%20%20%20a%20%5Blabel%3D%22Configure%20OpenAI%20and%20Pinecone%22%5D%3B%0A%20%20%20%20%20%20%20%20b%20%5Blabel%3D%22Create%20Pinecone%20index%22%5D%3B%0A%20%20%20%20%20%20%20%20c%20%5Blabel%3D%22Connect%20to%20the%20index%22%5D%3B%0A%20%20%20%20%20%20%20%20a%20-%3E%20b%20-%3E%20c%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20subgraph%20cluster_add_first_task%20%7B%0A%20%20%20%20%20%20%20%20label%20%3D%20%22Add%20First%20Task%22%3B%0A%20%20%20%20%20%20%20%20d%20%5Blabel%3D%22Define%20first_task%22%5D%3B%0A%20%20%20%20%20%20%20%20e%20%5Blabel%3D%22Call%20add_task(first_task)%22%5D%3B%0A%20%20%20%20%20%20%20%20d%20-%3E%20e%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20subgraph%20cluster_main_loop%20%7B%0A%20%20%20%20%20%20%20%20label%20%3D%20%22Main%20Loop%22%3B%0A%20%20%20%20%20%20%20%20f%20%5Blabel%3D%22Check%20if%20task_list%20is%20not%20empty%22%5D%3B%0A%20%20%20%20%20%20%20%20g%20%5Blabel%3D%22Print%20task%20list%22%5D%3B%0A%20%20%20%20%20%20%20%20h%20%5Blabel%3D%22Pop%20the%20first%20task%22%5D%3B%0A%20%20%20%20%20%20%20%20i%20%5Blabel%3D%22Execute%20task%20using%20execution_agent%22%5D%3B%0A%20%20%20%20%20%20%20%20j%20%5Blabel%3D%22Enrich%20and%20store%20result%20in%20Pinecone%22%5D%3B%0A%20%20%20%20%20%20%20%20k%20%5Blabel%3D%22Create%20new%20tasks%20using%20task_creation_agent%22%5D%3B%0A%20%20%20%20%20%20%20%20l%20%5Blabel%3D%22Re-prioritize%20task%20list%20using%20prioritization_agent%22%5D%3B%0A%20%20%20%20%20%20%20%20m%20%5Blabel%3D%22Repeat%22%5D%3B%0A%0A%20%20%20%20%20%20%20%20f%20-%3E%20g%20-%3E%20h%20-%3E%20i%20-%3E%20j%20-%3E%20k%20-%3E%20l%20-%3E%20m%3B%0A%20%20%20%20%20%20%20%20m%20-%3E%20f%20%5Bstyle%3D%22dashed%22%5D%3B%0A%20%20%20%20%7D%0A%0A%20%20%20%20cluster_init%20-%3E%20cluster_add_first_task%3B%0A%20%20%20%20cluster_add_first_task%20-%3E%20f%20%5Blhead%3Dcluster_main_loop%5D%3B%0A%7D%0A)
	- [current state](https://dreampuf.github.io/GraphvizOnline/#digraph%20G%20%7B%0A%20%20%20%20label%3D%22Main%20Loop%22%3B%0A%20%20%20%20node%20%5Bshape%3Drect%2C%20style%3Dfilled%2C%20fontname%3D%22Arial%22%2C%20fontsize%3D11%2C%20fillcolor%3D%22%23DDDDDD%22%5D%3B%0A%20%20%20%20subgraph%20cluster_agents%20%7B%0A%20%20%20%20%20%20%20%20label%3D%22Agents%22%3B%0A%20%20%20%20%20%20%20%20node%20%5Bfillcolor%3D%22lightblue%22%5D%3B%0A%20%20%20%20%20%20%20%201%20%5Blabel%3D%22Task%20Creation%20Agent%22%2C%20shape%3Drect%2C%20style%3Dfilled%2C%20color%3Dlightblue%5D%3B%0A%20%20%20%20%20%20%20%202%20%5Blabel%3D%22Prioritization%20Agent%22%2C%20shape%3Drect%2C%20style%3Dfilled%2C%20color%3Dlightblue%5D%3B%0A%20%20%20%20%20%20%20%203%20%5Blabel%3D%22Execution%20Agent%22%2C%20shape%3Drect%2C%20style%3Dfilled%2C%20color%3Dlightblue%5D%3B%0A%20%20%20%20%20%20%20%204%20%5Blabel%3D%22Context%20Agent%22%2C%20shape%3Drect%2C%20style%3Dfilled%2C%20color%3Dlightblue%5D%3B%0A%20%20%20%20%7D%0A%20%20%20%20node%20%5Bshape%3Drect%2C%20style%3Dfilled%2C%20fontname%3D%22Arial%22%2C%20fontsize%3D11%2C%20fillcolor%3D%22%23EEEEEE%22%5D%3B%0A%20%20%20%20a%20%5Blabel%3D%22Load%20Environment%20Variables%22%5D%3B%0A%20%20%20%20b%20%5Blabel%3D%22Parse%20Command%20Line%20Arguments%5Cn(if%20enabled)%22%5D%3B%0A%20%20%20%20c%20%5Blabel%3D%22Load%20dotenv%20extensions%5Cn(if%20enabled)%22%5D%3B%0A%20%20%20%20d%20%5Blabel%3D%22Print%20Configuration%22%5D%3B%0A%20%20%20%20e%20%5Blabel%3D%22Initialize%20OpenAI%20and%20Pinecone%5Cn(Connect%20to%20index)%22%5D%3B%0A%20%20%20%20f%20%5Blabel%3D%22Initialize%20Task%20Storage%5Cn(SingleTaskListStorage)%22%5D%3B%0A%20%20%20%20g%20%5Blabel%3D%22Add%20Initial%20Task%5Cn(if%20starting%20new%20objective)%22%5D%3B%0A%20%20%20%20h%20%5Blabel%3D%22Pull%20the%20first%20incomplete%20task%22%5D%3B%0A%20%20%20%20i%20%5Blabel%3D%22Execute%20Task%5Cn(Execution%20Agent)%22%5D%3B%0A%20%20%20%20j%20%5Blabel%3D%22Enrich%20Result%20and%20Store%20in%20Pinecone%22%5D%3B%0A%20%20%20%20k%20%5Blabel%3D%22Create%20New%20Tasks%20and%5CnReprioritize%20Task%20List%5Cn(Task%20Creation%20%26%20Prioritization%20Agents)%22%5D%3B%0A%20%20%20%20l%20%5Blabel%3D%22Repeat%5Cn(until%20tasks_storage%20is%20empty)%22%5D%3B%0A%0A%20%20%20%20a%20-%3E%20b%3B%0A%20%20%20%20b%20-%3E%20c%3B%0A%20%20%20%20c%20-%3E%20d%3B%0A%20%20%20%20d%20-%3E%20e%3B%0A%20%20%20%20e%20-%3E%20f%3B%0A%20%20%20%20f%20-%3E%20g%20%5Blabel%3D%22Add%20Initial%20Task%22%5D%3B%0A%20%20%20%20g%20-%3E%20h%20%5Blabel%3D%22Main%20Loop%5CnStart%22%5D%3B%0A%20%20%20%20h%20-%3E%203%20%5Blabel%3D%22Execute%20Task%22%5D%3B%0A%20%20%20%203%20-%3E%20i%20%5Blabel%3D%22Returned%20Task%20Result%22%5D%3B%0A%20%20%20%20i%20-%3E%20j%3B%0A%20%20%20%20j%20-%3E%204%20%5Blabel%3D%22Retrieve%20Context%22%5D%3B%0A%20%20%20%204%20-%3E%201%20%5Blabel%3D%22Returned%20Context%22%5D%3B%0A%20%20%20%201%20-%3E%20k%20%5Blabel%3D%22Create%20New%20Tasks%22%5D%3B%0A%20%20%20%20k%20-%3E%202%20%5Blabel%3D%22Reprioritize%20Tasks%22%5D%3B%0A%20%20%20%202%20-%3E%20l%20%5Blabel%3D%22Returned%20Prioritized%20Tasks%5Cn(Push%20to%20Task%20Storage)%22%5D%3B%0A%20%20%20%20l%20-%3E%20h%20%5Blabel%3D%22Repeat%22%5D%3B%0A%7D%0A)