# CPS
下面是使用 Markdown 格式整理的两个表格，第一个表格列出了常见的时序逻辑运算符，第二个表格则列出了 LTL 规格模式（模板）及其全局范围下的示例公式。

表1：常见的时序逻辑运算符

符号	英文名称	中文描述	示例表达式
□	Globally / Always	全局性要求，表示在所有时刻该命题均为真	□P 或 G P
◇	Eventually / Finally	最终性要求，表示在未来某个时刻该命题必然为真	◇P 或 F P
○ 或 X	Next	下一时刻要求，表示在紧接着的下一个状态该命题为真	○P 或 X P
U	Until	直到操作符，表示一个命题一直为真，直到另一命题为真	P U Q
W	Weak Until	弱直到，类似于 Until，但允许目标命题可能永远不发生	P W Q

表2：LTL 规格模式（模板）

模板	中文描述	示例公式（全局范围）	备注
Absence	事件 P 永远不发生	□¬P 或 G ¬P	可扩展为 Before R、After Q、Between Q and R 变体
Existence	事件 P 至少发生一次	◇P 或 F P	同样适用于其它范围（如在 R 之前出现等）
Universality	命题 P 始终为真	□P 或 G P	可与不同范围组合（Before/After/Between 等）
Precedence	事件 P 发生前必须先有事件 Q（即 P 只能在 Q 之后出现）	¬P W Q	W 为弱直到运算符；若 Q 从未发生，则 P 也不得发生
Response	每当事件 Q 发生时，事件 P 必须在其之后发生	□(Q → ◇P) 或 G (Q → F P)	可扩展为 Between 或 After 变体
Chain Response	每当事件 Q 发生时，事件 P 必须紧接着在下一时刻发生	□(Q → ○P) 或 G (Q → X P)	强调两事件在时间上的紧密相连
Chain Precedence	事件 P 发生时，其前一时刻必须为事件 Q（需要支持过去运算符）	□(P → Y Q)	Y 表示“上一时刻”，标准 LTL 不支持，需扩展运算符
Bounded Response	每当事件 Q 发生时，事件 P 必须在接下来的 k 个时刻内发生	□(Q → (X P ∨ X² P ∨ … ∨ Xᵏ P))	Xᵏ 表示连续 k 次“下一时刻”操作，适用于离散时间系统

说明：
	•	表2中的公式均为全局（Globally）范围下的基本表达，实际使用时可以结合不同的范围（如 Before R、After Q、Between Q and R）调整公式。
	•	这些规格模式的目标是帮助将自然语言需求转化为形式化的 LTL 公式，从而便于利用模型检测等工具进行验证。

希望这两个表格能帮助你快速查阅常用的时序逻辑符号和 LTL 规格模板！
