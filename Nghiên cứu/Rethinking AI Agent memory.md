|     | Rethinking |     |     | Memory |     | as Continuously |     | Evolving |     | Connectivity |     |     |     |
| --- | ---------- | --- | --- | ------ | --- | --------------- | --- | -------- | --- | ------------ | --- | --- | --- |
JizhanFang1,2,BuqiangXu1,ZhixianWang1,HaoliangCao2,XinleDeng1,
BaohuaDong2,HangchengZhu2,RuohuiHuang2,GangYu2,YingWei1,
GuozhouZheng1,FeiyuXiong3,HaofenWang4,HuajunChen1,NingyuZhang1*
1ZhejiangUniversity 2AlibabaGroup 3MemTensor 4TongjiUniversity
Abstract
Existingmemory-augmentedLLMagentsof-
6202 yaM 72  ]LC.sc[  1v37782.5062:viXra
| ten | treat | memory | as a | static | repository | with |     |     |     |     |     |     |     |
| --- | ----- | ------ | ---- | ------ | ---------- | ---- | --- | --- | --- | --- | --- | --- | --- |
pre-definedrepresentationsandfixedretrieval
| pipelines, |              | which                | is brittle | in        | dynamic      | agen-  |     |     |     |     |     |     |     |
| ---------- | ------------ | -------------------- | ---------- | --------- | ------------ | ------ | --- | --- | --- | --- | --- | --- | --- |
| tic        | environments |                      | where      | feedback, | task         | varia- |     |     |     |     |     |     |     |
| tion,      | and          | heterogeneoussignals |            |           | continuously |        |     |     |     |     |     |     |     |
reshapewhatshouldberememberedandhow
| it      | should        | be connected. |       | To address            |        | this, we |     |     |     |     |     |     |     |
| ------- | ------------- | ------------- | ----- | --------------------- | ------ | -------- | --- | --- | --- | --- | --- | --- | --- |
| propose |               | FluxMem,      | a     | connectivity-evolving |        |          |     |     |     |     |     |     |     |
| memory  |               | framework     | that  | models                | memory | as       |     |     |     |     |     |     |     |
| a       | heterogeneous |               | graph | and progressively     |        | re-      |     |     |     |     |     |     |     |
fines its topology through three stages: ini- Figure1: Thefailuresofstaticmemorysystems.
tialconnectionformation,feedback-drivenre-
finement, and long-term consolidation. Dur- agents,memoryeffectivenessultimatelydepends
ingexecution,FluxMemrepairsmissinglinks,
|     |     |     |     |     |     |     | on whether |     | the | most useful | memories |     | can be |
| --- | --- | --- | --- | --- | --- | --- | ---------- | --- | --- | ----------- | -------- | --- | ------ |
prunes interference, aligns abstraction granu- accessed at each decision step, as sufficiently
larity,anddistillsrecurrentsuccessfultrajecto-
|      |      |          |            |     |           |        | useful | memory | context |     | substantially | improves |     |
| ---- | ---- | -------- | ---------- | --- | --------- | ------ | ------ | ------ | ------- | --- | ------------- | -------- | --- |
| ries | into | reusable | procedural |     | circuits, | guided |        |        |         |     |               |          |     |
subtasksuccess.
byonemetricformemorygeneralizabilityand
evolutionarymaturity. Acrossthreefundamen- We formalize such usefulness as a problem of
tallydistinctbenchmarksincludingLoCoMo, memoryconnectivity. Drawingfromcognitivesci-
| Mind2Web, |     | and | GAIA, | FluxMem |     | achieves |     |     |     |     |     |     |     |
| --------- | --- | --- | ----- | ------- | --- | -------- | --- | --- | --- | --- | --- | --- | --- |
ence(Hebb,2005;FranklandandBontempi,2005),
consistentstate-of-the-artperformance,demon-
wedefinememoryasthelong-termsedimentation
stratingstrongadaptationandgeneralizationin
|                             |     |     |     |     |             |     | of memory |     | units | and their | connections, |     | contin- |
| --------------------------- | --- | --- | --- | --- | ----------- | --- | --------- | --- | ----- | --------- | ------------ | --- | ------- |
| complexagenticenvironments. |     |     |     |     | Thecodewill |     |           |     |       |           |              |     |         |
beopen-sourcedinthenearfuture1. uouslyshapedthroughenvironmentalinteraction.
|                |              |     |         |     |        |        | Mirroring                          | human     |           | cognitive | processes, | this      | struc-    |
| -------------- | ------------ | --- | ------- | --- | ------ | ------ | ---------------------------------- | --------- | --------- | --------- | ---------- | --------- | --------- |
| 1 Introduction |              |     |         |     |        |        | turalevolutionoperatesontwolevels. |           |           |           |            | Attheunit |           |
|                |              |     |         |     |        |        | level,                             | the brain | generates |           | new units  | for       | novel in- |
| For            | long-horizon |     | agents, |     | memory | mecha- |                                    |           |           |           |            |           |           |
formationandcontinuouslyreshapesexistingunits
nism(Zhangetal.,2025c;Huetal.,2026b)plays bymodifyingtheirinternalcontent. Thisensures
| a central | role | (Mei | et al., | 2025), | by  | distilling |     |     |     |     |     |     |     |
| --------- | ---- | ---- | ------- | ------ | --- | ---------- | --- | --- | --- | --- | --- | --- | --- |
thateachmemoryunitdynamicallyintegratesnew
| useful | factual | information, |     | reusable |     | experiences |     |     |     |     |     |     |     |
| ------ | ------- | ------------ | --- | -------- | --- | ----------- | --- | --- | --- | --- | --- | --- | --- |
experiencesandrefinesitssemanticrepresentation.
and skills from the agent’s past interaction Attheconnectionlevel,operationsarestrictlytask-
trajectories (Packer et al., 2024; Wei et al., 2025; centric, the system establishes links between co-
| Zhang | et al., | 2026a), | storing |     | them | in diverse |     |     |     |     |     |     |     |
| ----- | ------- | ------- | ------- | --- | ---- | ---------- | --- | --- | --- | --- | --- | --- | --- |
activatedunitstoformfunctionalassociations,and
memoryforms,andretrievingrelevantmemories
pruneslinksthatproveirrelevant,maintainingan
when similar tasks arise to support downstream efficient associative network. Through repeated
| problem | solving | and | agent | evolving |     | (Qi et al., |     |     |     |     |     |     |     |
| ------- | ------- | --- | ----- | -------- | --- | ----------- | --- | --- | --- | --- | --- | --- | --- |
taskexecutionandenvironmentalfeedback,these
2026;angGaoetal.,2026;Qiuetal.,2025;Wang
localizedupdatesgraduallyconsolidateintostable,
et al., 2026; Ye et al., 2026). For long-horizon large-scale regions of interconnected nodes and
|     |     |     |     |     |     |     | edges. | Rather | than | static | storage, | memory | thus |
| --- | --- | --- | --- | --- | --- | --- | ------ | ------ | ---- | ------ | -------- | ------ | ---- |
* Correspondingauthor.
1https://github.com/zjunlp/LightMem. emergesasaself-organizingstructurethatitsmem-

oryunitsandconnectionscontinuouslyadaptand Connection Formation rapidly establishes tenta-
evolveovertime(KellyandGaravan,2005). tive cross-layer associations for novel tasks. (2)
|             |     |        |         |             |      | Feedback-Driven |     | Refinement |     | employs | a closed- |
| ----------- | --- | ------ | ------- | ----------- | ---- | --------------- | --- | ---------- | --- | ------- | --------- |
| Challenges. |     | First, | Failure | of Adaptive | Mem- |                 |     |            |     |         |           |
loopmechanismtoiterativelyeditsubgraphtopol-
| oryConnectivity. |     | Existingmethodspredominantly |     |     |     |               |     |         |        |         |               |
| ---------------- | --- | ---------------------------- | --- | --- | --- | ------------- | --- | ------- | ------ | ------- | ------------- |
|                  |     |                              |     |     |     | ogy, creating |     | missing | links, | pruning | interference, |
relyonstatic,hand-craftedpipelines(Yangetal.,
orconditionallybypassingmemoryuntilexecution
| 2026; Chhikara     |      | et al., | 2025;                 | Fang | et al., 2025b; |            |              |           |     |               |          |
| ------------------ | ---- | ------- | --------------------- | ---- | -------------- | ---------- | ------------ | --------- | --- | ------------- | -------- |
|                    |      |         |                       |      |                | succeeds.  | (3)          | Long-Term |     | Consolidation | clusters |
| Suzgunetal.,2026). |      |         | Byhardcodingmemoryop- |      |                |            |              |           |     |               |          |
|                    |      |         |                       |      |                | successful | trajectories |           | to  | induce stable | procedu- |
| erations,          | they | assume  | rigid designs         |      | and fixed op-  |            |              |           |     |               |          |
ralcircuits,monitoredbyaconvergencematurity
| erations | generalize | across | tasks. | However, | such |     |     |     |     |     |     |
| -------- | ---------- | ------ | ------ | -------- | ---- | --- | --- | --- | --- | --- | --- |
metric. Ashigh-utilitypathwayscrystallize,recur-
staticparadigmscannotestablishoptimalmemory
ringtasksbypassredundantretrievalanddirectly
structuresfordiversescenariosordynamicallyre-
|     |     |     |     |     |     | activate | mature | subgraphs. |     | This pipeline | trans- |
| --- | --- | --- | --- | --- | --- | -------- | ------ | ---------- | --- | ------------- | ------ |
finethembasedonenvironmentalfeedback(Zhang
formsstaticmemorystorageintoaself-optimizing
| et al., 2025b; |     | Chen | et al., 2026b). |     | This inflexi- |     |     |     |     |     |     |
| -------------- | --- | ---- | --------------- | --- | ------------- | --- | --- | --- | --- | --- | --- |
connectivitysubstratethatcontinuouslyadaptsto
| bility creates |     | bottlenecks | at both | the | connection |     |     |     |     |     |     |
| -------------- | --- | ----------- | ------- | --- | ---------- | --- | --- | --- | --- | --- | --- |
evolvingtaskdemands.
| andunitlevels: |     | (1)InaccurateMemoryConnec- |     |     |     |     |     |     |     |     |     |
| -------------- | --- | -------------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
tions. Thisinaccuracyprimarilymanifestsduring Results. WeevaluateFluxMemonthreebench-
| memoryretrieval. |     | Itleadstotwoconcretefailures: |     |     |     |       |          |          |     |                |          |
| ---------------- | --- | ----------------------------- | --- | --- | --- | ----- | -------- | -------- | --- | -------------- | -------- |
|                  |     |                               |     |     |     | marks | covering | distinct |     | task scenarios | to eval- |
under-connection,wherecriticallinksaremissed
|     |     |     |     |     |     | uate generalization: |     |     | LoCoMo | (Maharana | et al., |
| --- | --- | --- | --- | --- | --- | -------------------- | --- | --- | ------ | --------- | ------- |
duetoretrievalimprecision,deprivingtheagentof 2024)(long-contextreasoning),Mind2Web(Deng
| essential | context, | and | over-connection, |     | where ir- |         |       |             |     |                  |     |
| --------- | -------- | --- | ---------------- | --- | --------- | ------- | ----- | ----------- | --- | ---------------- | --- |
|           |          |     |                  |     |           | et al., | 2023) | (real-world |     | web navigation), | and |
relevantassociationsareindiscriminatelyretrieved,
|     |     |     |     |     |     | GAIA | (Mialon | et  | al., 2023) | (general | assistant |
| --- | --- | --- | --- | --- | --- | ---- | ------- | --- | ---------- | -------- | --------- |
introducingnoiseandhallucinations(Jiangetal.,
tasks). FluxMemachievesstate-of-the-artperfor-
2025; Chen et al., 2026a). Fundamentally, static manceacrossallthreebenchmarks. OnLoCoMo,
| pipelines | lack | the dynamic | adaptability |     | required |     |     |     |     |     |     |
| --------- | ---- | ----------- | ------------ | --- | -------- | --- | --- | --- | --- | --- | --- |
FluxMemreaches95.06averageaccuracy,above
| for precise | connection |     | formation | and | access. (2) |                                |     |     |     |            |     |
| ----------- | ---------- | --- | --------- | --- | ----------- | ------------------------------ | --- | --- | --- | ---------- | --- |
|             |            |     |           |     |             | theFullContextbaseline(81.23). |     |     |     | OnMind2Web |     |
InflexibleMemoryUnitContent. Existingsystems intherealisticsetting(nomanualelementfiltering),
representmemoryunitsatasingle,predefinedlevel
FluxMemimprovesCross-Tasksuccessrateto8.1,
| of abstraction. |     | When | unit content | is  | misaligned, |           |     |       |     |                |           |
| --------------- | --- | ---- | ------------ | --- | ----------- | --------- | --- | ----- | --- | -------------- | --------- |
|                 |     |      |              |     |             | more than | AWM | (Wang |     | et al., 2024c) | (3.6). On |
eitherexcessivelycoarse,losingcriticalexecution
|     |     |     |     |     |     | GAIA, | FluxMem |     | increases | the average | success |
| --- | --- | --- | --- | --- | --- | ----- | ------- | --- | --------- | ----------- | ------- |
details,oroverlyfine,obscuringhigh-levelstruc- rate from 52.12 to 64.85 on Kimi K2 (+12.73%
turalpatterns,thememoryunitfailstoadaptively
absolute)comparedwiththeFlash-Searcher(Qin
integratenewexperiences.
etal.,2025)baseline,andalsosurpassesthestrong
Second, Failure of Memory Connection Con- MemEvolve(Zhangetal.,2025b)baseline.
| solidation. | While | existing | systems |     | preserve task |     |     |     |     |     |     |
| ----------- | ----- | -------- | ------- | --- | ------------- | --- | --- | --- | --- | --- | --- |
trajectories(Fangetal.,2026;Ouyangetal.,2025;
2 FluxMemMemoryArchitecture
| Tang et | al., 2025a), |     | they treat | memories | as iso- |     |     |     |     |     |     |
| ------- | ------------ | --- | ---------- | -------- | ------- | --- | --- | --- | --- | --- | --- |
2.1 Three-LayerMemoryGraph
| lated instances                |                                    | rather  | than progressively |                  | consoli-     |                            |         |     |                    |                 |       |
| ------------------------------ | ---------------------------------- | ------- | ------------------ | ---------------- | ------------ | -------------------------- | ------- | --- | ------------------ | --------------- | ----- |
| datingthem.                    | Trueconsolidationrequireslocalized |         |                    |                  |              |                            |         |     |                    |                 |       |
|                                |                                    |         |                    |                  |              | We model                   | FluxMem |     | as                 | a heterogeneous | graph |
| updates                        | to coalesce                        | through | feedback           |                  | into stable, |                            |         |     |                    |                 |       |
|                                |                                    |         |                    |                  |              | G = (V,E),wherethenodesetV |         |     |                    | comprisesthree  |       |
| large-scaleassociativeregions. |                                    |         |                    | Lackingthismech- |              |                            |         |     |                    |                 |       |
|                                |                                    |         |                    |                  |              | functionallayers.          |         | ⃝1  | SemanticKnowledgeV |                 | sem   |
anism,agentsrepeatedlyreconstructsimilarassoci-
|     |     |     |     |     |     | stores static | factual |     | knowledge | that | provides evi- |
| --- | --- | --- | --- | --- | --- | ------------- | ------- | --- | --------- | ---- | ------------- |
ationsinsteadofinternalizingenduringstructural
dentialsupport(e.g.,knowledgedocumentsortheir
| patterns, | preventing | memory |     | networks | from self- |                       |     |     |     |                     |     |
| --------- | ---------- | ------ | --- | -------- | ---------- | --------------------- | --- | --- | --- | ------------------- | --- |
|           |            |        |     |          |            | correspondingchunks). |     |     | ⃝2  | EpisodicExperiences |     |
organizingintooptimalconfigurations. V recordsconcretestate-actiontrajectories(e.g.,
epi
|         |     |         |                   |     |         | debugginglogsortool-usesequences). |     |     |     |     | ⃝3 Proce- |
| ------- | --- | ------- | ----------------- | --- | ------- | ---------------------------------- | --- | --- | --- | --- | --------- |
| Method. | To  | address | these challenges, |     | we pro- |                                    |     |     |     |     |           |
pose FluxMem, a connectivity-evolving frame- duralSkillsV encapsulatesdistilledreasoning
proc
work that models memory as a dynamically templates(e.g.,multi-stepplanningheuristics).
|          |               |     |       |        |           | Among | the | 3 layers, | V   | serves | as the opera- |
| -------- | ------------- | --- | ----- | ------ | --------- | ----- | --- | --------- | --- | ------ | ------------- |
| editable | heterogeneous |     | graph | across | semantic, |       |     |           |     | epi    |               |
episodic, and procedural layers. Context is for- tionalnexusthatorchestratestheinterplaybetween
malizedasanactivatedsubgraphrefinedthrough static knowledge and distilled skills. Each node
(q)
a three-stage evolutionary pipeline. (1) Initial v ∈ V representsaspecifictaskq andrecords
epi epi

Figure2:TheFluxMemarchitecture.StagesIandIIoperateonlineatastep-wisegranularity. StageIIIisconducted
offline,aimingforimmediateperformanceoptimizationandlong-termmemoryconsolidation,respectively.
)}T
its full step-by-step trajectory τ q = {(o t ,a t . In this formula, Obs t describes the observations.
t=1
The three layers are linked in a bottom-up order Under this formulation, optimizing the working
through two types of edges in E. First, during contextisequivalenttoperformingtargetedtopo-
task execution, the agent retrieves relevant facts logical edits on G t (q), as the prompt content is
from V to explain its current observation and strictly determined by the activated node set and
sem
decide the next step. This creates the edge set edge connections. Consequently, the adaptation
( q )
E ⊆ V ×V , where an edge (v ,v ) pipelinesystematicallyevolvesG (q)fromfragile
| ground | sem | epi |     |     | sem | e p i |     |     |     |     |     | t   |     |
| ------ | --- | --- | --- | --- | --- | ----- | --- | --- | --- | --- | --- | --- | --- |
simply indicates that a specific fact provides evi- tentativelinksintorobust,task-optimizedcircuits
throughthreesequentialstages.
| dential support |     | for a   | step in task | q.     | Second, | after |     |                            |     |     |     |     |     |
| --------------- | --- | ------- | ------------ | ------ | ------- | ----- | --- | -------------------------- | --- | --- | --- | --- | --- |
| completing      | one | or more | similar      | tasks, | the     | agent |     |                            |     |     |     |     |     |
|                 |     |         |              |        |         |       | 3   | Three-StageMemoryEvolution |     |     |     |     |     |
identifiescommonpatternsinthesetrajectoriesand
summarizesthemintoreusableskills. Thisforms FluxMem comprises three stages. Stages I and
| theedgesetE |     | ⊆   | V ×V | , whereanedge |     |     |     |     |     |     |     |     |     |
| ----------- | --- | --- | ---- | ------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
distill epi proc IIoperateonlineatastep-wisegranularityduring
| (q)        |                                     |     |     |     |     |     | taskexecution. |     | Ateachtimestept,StageIisexe- |     |     |     |     |
| ---------- | ----------------------------------- | --- | --- | --- | --- | --- | -------------- | --- | ---------------------------- | --- | --- | --- | --- |
| (v ,v proc | )showsthataskillisdistilledfrompast |     |     |     |     |     |                |     |                              |     |     |     |     |
epi
experiences. Once created, v ∈ V can be cutedfirsttogenerateS (q),whichisimmediately
|     |     |     |     | proc | proc |     |     |     |     | t   |     |     |     |
| --- | --- | --- | --- | ---- | ---- | --- | --- | --- | --- | --- | --- | --- | --- |
usedtoguidetheagentinfuturetasks. processedbyStageIItoyieldtherefinedcontext
S′(q).
InFluxMem, thesemanticlayerissourceddi- StageIIIisconductedoffline.
t
| rectly from | the | environment, |     | encompassing |     | raw |     |                                   |     |     |     |     |     |
| ----------- | --- | ------------ | --- | ------------ | --- | --- | --- | --------------------------------- | --- | --- | --- | --- | --- |
|             |     |              |     |              |     |     | 3.1 | StageI:InitialConnectionFormation |     |     |     |     |     |
inputssuchasdialoguehistoriesandtoolAPIdoc-
|             |                                     |             |            |     |       |       | SemanticConnectionRetrieval. |     |     |     |                  | Attimestept, |     |
| ----------- | ----------------------------------- | ----------- | ---------- | --- | ----- | ----- | ---------------------------- | --- | --- | --- | ---------------- | ------------ | --- |
| umentation. | Episodenodesareinstantiatedindivid- |             |            |     |       |       |                              |     |     |     |                  |              |     |
|             |                                     |             |            |     |       |       | giventhecurrentobservationo  |     |     |     | ,thesystemestab- |              |     |
| ually for   | each                                | task, while | procedural |     | skill | nodes |                              |     |     |     | t                |              |     |
aresubsequentlyinducedinsection3.3. lishesinitialassociationsbetweeno andsupport-
t
|     |     |     |     |     |     |     | ing | factual | knowledge | by  | querying | the | semantic |
| --- | --- | --- | --- | --- | --- | --- | --- | ------- | --------- | --- | -------- | --- | -------- |
2.2 ContextasDynamicallyInduced layerV . Wecomputeahybridrelevancescore
sem
| Connectivity |     |     |     |     |     |     | for | each candidate |     | v ∈ V | by  | fusing | dense em- |
| ------------ | --- | --- | --- | --- | --- | --- | --- | -------------- | --- | ----- | --- | ------ | --------- |
sem
Ateachsteptoftaskq,FluxMemconstructsthe bedding similarity, sparse lexical matching, and
LLM-basedverification:
| agent’s | context | S (q). | The | system | dynamically |     |     |     |     |     |     |     |     |
| ------- | ------- | ------ | --- | ------ | ----------- | --- | --- | --- | --- | --- | --- | --- | --- |
t
v·o
| selects a       | task-specific |                            | subset  | of nodes     | to  | form a |     |           |      |       | t         |     |     |
| --------------- | ------------- | -------------------------- | ------- | ------------ | --- | ------ | --- | --------- | ---- | ----- | --------- | --- | --- |
|                 |               |                            |         |              |     |        |     | Score(v,o | ) =  |       | +BM25(v,o |     | )   |
| localsubgraphG  |               | (q)                        | = (V ,E | ) ⊂ G,whereV |     | =      |     |           | t    | ∥v∥∥o | ∥         |     | t   |
|                 |               | t                          | t       | t            |     | t      |     |           |      |       | t         |     |     |
| Vsem∪Vepi∪Vproc |               | containstheactivatedmemory |         |              |     |        |     |           |      |       |           |     |     |
| t               | t             | t                          |         |              |     |        |     |           | +LLM |       | (v,o ).   |     |     |
|                 |               |                            |         |              |     |        |     |           |      | ver   | t         |     |     |
nodesfromthethreelayers.
|     |     |     |     |     |     |     | The | top-k | nodes instantiate |     | Vsem, | with | directed |
| --- | --- | --- | --- | --- | --- | --- | --- | ----- | ----------------- | --- | ----- | ---- | -------- |
t
|     |     |     | Vsem, | Vepi, | Vproc), |     |     |     |     |     |     |     |     |
| --- | --- | --- | ----- | ----- | ------- | --- | --- | --- | --- | --- | --- | --- | --- |
S (q) = Concat(q, Obs , edges Esem = {(v ,v) | v ∈ Vsem} established to
| t   |     |     | t   | t   | t   | t   |     | t   | t   |     | t   |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

linkthemtothecurrentstepanchorv t . ContentReshapingforGranularityAlignment.
Whenretrievalissufficientbuttheunitabstraction
| EpisodicConnectionRetrieval. |      |      |         |        | Todrawonex- |     |            |     |         |         |        |        |        |
| ---------------------------- | ---- | ---- | ------- | ------ | ----------- | --- | ---------- | --- | ------- | ------- | ------ | ------ | ------ |
|                              |      |      |         |        |             |     | mismatches |     | current | demands | (e.g., | overly | coarse |
| perience                     | from | past | similar | tasks, | we query    | the |            |     |         |         |        |        |        |
forpreciseexecutionoroverlyfineforhigh-level
| episodic | layer | V   | for the | k most | relevant | past |            |     |            |            |          |     |         |
| -------- | ----- | --- | ------- | ------ | -------- | ---- | ---------- | --- | ---------- | ---------- | -------- | --- | ------- |
|          |       | epi |         |        |          |      | planning), |     | the system | adaptively | modifies |     | the in- |
episodesusingembeddingsimilarity.
|     |     |     |     |     |     |     | ternal | content | of v | ∈ V . | This | involves | either |
| --- | --- | --- | --- | --- | --- | --- | ------ | ------- | ---- | ----- | ---- | -------- | ------ |
|     |     |     |     |     |     |     |        |         | old  | t     |      |          |        |
Vepi (cid:8) (cid:9) expandingv withfiner-grainedexecutiondetails
|     |     | = TopK |         | cos(u,o | )   | .   |     |     | old |     |     |     |     |
| --- | --- | ------ | ------- | ------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
|     | t   |        | u∈V epi |         | t   |     |     |     |     |     |     |     |     |
orabstractingredundantcomponentstoelevateits
|                                  |     |     |     |     |     |         | semantic | level, | yielding | a refined |     | unit v | . The |
| -------------------------------- | --- | --- | --- | --- | --- | ------- | -------- | ------ | -------- | --------- | --- | ------ | ----- |
| ProceduralConnectionInheritance. |     |     |     |     |     | Basedon |          |        |          |           |     |        | align |
the retrieved episodes V epi , we collect applicable local subgraph is updated by replacing v with
|     |     |     | t   |     |     |     |     |     |     |     |     |     | old |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
skillsbytraversingexistingdistillationconnections. v whilepreservingestablishedconnections.
align
Afterapplyingthetargetededits,therefinedsub-
| Specifically,weselectallskillnodesv |     |     |     |     |     | thatare |     |     |     |     |     |     |     |
| ----------------------------------- | --- | --- | --- | --- | --- | ------- | --- | --- | --- | --- | --- | --- | --- |
proc
|                                 |     |          |     |     |         |         | graphG′ | =   | (V′,E′)isserializedintotheupdated |            |     |     |          |
| ------------------------------- | --- | -------- | --- | --- | ------- | ------- | ------- | --- | --------------------------------- | ---------- | --- | --- | -------- |
| linkedtoanyretrievedepisodeviaE |     |          |     |     | distill | :       |         | t   | t t                               |            |     |     |          |
|                                 |     |          |     |     |         |         | context | S′  | for subsequent                    | reasoning. |     |     | The loop |
|                                 |     | (cid:91) |     |     |         |         |         | t   |                                   |            |     |     |          |
| Vproc                           |     | (cid:8)  |     |     |         | (cid:9) |         |     |                                   |            |     |     |          |
= v proc | (v epi ,v proc ) ∈ E distill . terminates upon execution success or reaching a
t
predefinedrefinementroundsT.
v ∈Vepi
epi t
The retrieved facts, episodes, and skills together 3.3 StageIII:Long-TermConnection
| formtheinitialstep-localsubgraphG |     |     |     |     | =   | (V ,E ), |     | Consolidation |     |     |     |     |     |
| --------------------------------- | --- | --- | --- | --- | --- | -------- | --- | ------------- | --- | --- | --- | --- | --- |
|                                   |     |     |     |     | t   | t t      |     |               |     |     |     |     |     |
Vsem∪Vepi∪Vproc
whereV = . Thissubgraphis EpisodicClusteringandSkillInduction. Upon
|     | t   | t   | t   | t   |     |     |     |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
serializedintotheinitialstepcontextS . Although task completion, trajectories are committed as
t
thisprovidesacompletestartingpointforthecur-
|     |     |     |     |     |     |     | episodicnodesv |     | τ ∈ | V epi . Duringofflineconsolida- |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | -------------- | --- | --- | ------------------------------- | --- | --- | --- |
rentstep’sreasoning,theselectedconnectionsare tion,thesystemfirstpartitionsV intoM clusters
epi
preliminaryandwillberefinedinStageII. {C }M basedonsemantictrajectorysimilarity,
m m=1
computedviacosinedistancebetweenepisodeem-
3.2 StageII:Feedback-DrivenConnectivity
|     |     |     |     |     |     |     | beddingsu |     | . ForeachclusterC |     | ,anLLM-based |     |     |
| --- | --- | --- | --- | --- | --- | --- | --------- | --- | ----------------- | --- | ------------ | --- | --- |
|     |     |     |     |     |     |     |           |     | τ                 |     | m            |     |     |
Refinement
inductionoperatorextractstheskillsorreasoning
Followingtheinitialretrieval,thesystemaddresses pattern shared across episodes, abstracting them
| structuralmisalignmentsthroughafeedback-driven |     |                             |               |     |         |     |                                    |     |     |     | (m)  |     |       |
| ---------------------------------------------- | --- | --------------------------- | ------------- | --- | ------- | --- | ---------------------------------- | --- | --- | --- | ---- | --- | ----- |
|                                                |     |                             |               |     |         |     | intoanewproceduralskillnodev       |     |     |     |      | ∈   | V .   |
|                                                |     |                             |               |     |         |     |                                    |     |     |     | proc |     | proc  |
| refinementloop.                                |     | Atstept,uponreceivingexecu- |               |     |         |     |                                    |     |     |     |      |     |       |
|                                                |     |                             |               |     |         |     | PEMS-GuidedIterativeConsolidation. |     |     |     |      |     | Since |
| tion feedback                                  |     | f t (from                   | environmental |     | signals | or  |                                    |     |     |     |      |     |       |
self-verification),theagentattributesreasoningfail- previousinitialskillinductionisone-wayandmay
urestoeitherconnection-levelorunit-levelflaws produceinvalidskills,weverifyandoptimizethem
throughaclosed-looprefinementprocessguidedby
| andappliestargetededitstoG |     |     |     | .   |     |     |     |     |     |     |     |     |     |
| -------------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
t
|                  |     |     |             |     |            |     | iterativeevolution.       |     | Ateachiterationk,thesystem |     |                   |     |     |
| ---------------- | --- | --- | ----------- | --- | ---------- | --- | ------------------------- | --- | -------------------------- | --- | ----------------- | --- | --- |
| Connection-Level |     |     | Refinement. |     | To resolve | in- |                           |     |                            |     |                   |     |     |
|                  |     |     |             |     |            |     | re-runsthesourceepisodesC |     |                            |     | thatgeneratedeach |     |     |
m
accuratememoryconnections,thesystemdynami- skill v , using the current skill version as guid-
proc
callyadjuststheassociativetopologybasedonfeed-
|                  |     |                           |     |     |     |     | ance. | We  | then compute | the | Procedure | Evolution |     |
| ---------------- | --- | ------------------------- | --- | --- | --- | --- | ----- | --- | ------------ | --- | --------- | --------- | --- |
| backattribution. |     | (i)LinkExpansionforUnder- |     |     |     |     |       |     |              |     |           |           |     |
MaturityScore(PEMS)foreveryskill:
| Connection. |     | Iff indicatesmissingcriticalcontext, |     |     |     |     |     |     |     |     |     |     |     |
| ----------- | --- | ------------------------------------ | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
t
|     |     |     |     |     |     |     |     |     | (cid:0) (k)(cid:1) |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | ------------------ | --- | --- | --- | --- |
the system identifies semantically proximate but η V (cid:16) (cid:17)
|                                    |       |     |     |     |                 |           | PEMS(k)   |     | pro                                | c           | (cid:0) | ( k )   | ( k − 1)(cid:1) |
| ---------------------------------- | ----- | --- | --- | --- | --------------- | --------- | --------- | --- | ---------------------------------- | ----------- | ------- | ------- | --------------- |
| unactivated                        | nodes | v   | ∈ V | \V  | and establishes |           |           | =   |                                    | ×           | 1−δ G   | ,G      | ,               |
|                                    |       |     | new | t   |                 |           |           |     | (cid:0)                            | ( k)(cid:1) |         | c o n s | c o n s         |
|                                    |       |     |     |     |                 |           |           |     | logℓ V                             |             |         |         |                 |
| newtask-centricedgesviaE           |       |     |     | ← E | ∪{(v            | ,v )}.    |           |     | proc                               |             |         |         |                 |
|                                    |       |     |     | t t |                 | t new     |           |     |                                    |             |         |         |                 |
| (ii)LinkPruningforOver-Connection. |       |     |     |     |                 | Iff t re- |           |     |                                    |             |         |         |                 |
|                                    |       |     |     |     |                 |           | whereη(k) |     | istheaveragesuccessrateofthesource |             |         |         |                 |
vealscontextcongestionorhallucinatedguidance,
|            |            |     |            |       |       |     | episodes                     | under | the current | skill, | ℓ(k) | is  | the token |
| ---------- | ---------- | --- | ---------- | ----- | ----- | --- | ---------------------------- | ----- | ----------- | ------ | ---- | --- | --------- |
| the system | identifies |     | distractor | edges | E     | ⊂ E |                              |       |             |        |      |     |           |
|            |            |     |            |       | noise | t   | lengthoftheskilltext,andδ(k) |       |             |        |      |     |           |
measurestheem-
| and severs | them | via | E ← E | \E      | , isolating | v   |                                             |     |     |     |     |     |     |
| ---------- | ---- | --- | ----- | ------- | ----------- | --- | ------------------------------------------- | --- | --- | --- | --- | --- | --- |
|            |      |     | t     | t noise |             | t   | beddingdifferencebetweenthecurrentandprevi- |     |     |     |     |     |     |
fromirrelevantassociations.
|     |     |     |     |     |     |     | ousskillversions. |     | Basedontheexecutionresults, |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | ----------------- | --- | --------------------------- | --- | --- | --- | --- |
Unit-LevelRefinement. Toovercomeinflexible theLLMdirectlyrewriteslow-scoringskillstofix
memory unit content, the system dynamically re- logical errors or remove redundant content. This
shapes internal representations when granularity test-score-refine cycle repeats until the score im-
provement∆PEMS(k)
misalignment impedes step-level reasoning. (iii) fallsbelowϵ. Atthatpoint,

Method Single Multi Temp Open AVG 2025),⃝7 Flash-Searcher(Qinetal.,2025),and⃝8
|     |     | Hop | Hop |     | Do- |     | MemEvolve(Zhangetal.,2025b). |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | ---------------------------- | --- | --- | --- | --- | --- | --- |
main
|     |     | GPT-4.1-mini |     |     |     |     | Metrics. | ForLoCoMo,wereporttheLLM-as-a- |     |     |     |     |     |
| --- | --- | ------------ | --- | --- | --- | --- | -------- | ------------------------------ | --- | --- | --- | --- | --- |
ForMind2Web,weevaluate
| FullContext |     | 87.99 | 80.50 | 71.03 | 58.33 | 81.23 | judge(LMJ)score. |     |     |     |     |     |     |
| ----------- | --- | ----- | ----- | ----- | ----- | ----- | ---------------- | --- | --- | --- | --- | --- | --- |
Zep 66.90 53.70 60.20 43.80 61.60 action-levelaccuracywithElementAccuracy(EA),
| Mem0  |     | 71.40 | 68.20 | 56.90 | 47.90 | 66.30 |        |           |      |         |      |        |     |
| ----- | --- | ----- | ----- | ----- | ----- | ----- | ------ | --------- | ---- | ------- | ---- | ------ | --- |
|       |     |       |       |       |       |       | Action | F1 (AF1), | Step | Success | Rate | (SSR), | and |
| A-Mem |     | 77.41 | 61.35 | 71.03 | 50.00 | 71.43 |        |           |      |         |      |        |     |
MemoryOS 78.95 66.67 55.45 60.42 70.65 report overall Success Rate (SR) for completing
Nemori 87.16 77.30 76.32 55.21 81.10 a full navigation task. For GAIA, we use Suc-
| LightMem |     | 87.87 | 76.95 | 80.37 | 57.29 | 82.40 |     |     |     |     |     |     |     |
| -------- | --- | ----- | ----- | ----- | ----- | ----- | --- | --- | --- | --- | --- | --- | --- |
cessRateacrossLevel1–3tomeasureend-to-end
| MIRIX |     | 85.11 | 83.70 | 88.39 | 65.62 | 85.38 |     |     |     |     |     |     |     |
| ----- | --- | ----- | ----- | ----- | ----- | ----- | --- | --- | --- | --- | --- | --- | --- |
EverMemOS 96.67 91.84 89.72 76.04 93.05 taskcompletionunderincreasingdifficulty. Further
statisticsandexperimentaldetailsaboutbaselines
| FluxMem |     | 95.95 | 93.26 | 95.64 | 90.62 | 95.06 |     |     |     |     |     |     |     |
| ------- | --- | ----- | ----- | ----- | ----- | ----- | --- | --- | --- | --- | --- | --- | --- |
areprovidedinAppendixA.1.
Qwen3-30B-A3B-2507-Instruct
| FullContext |     | 87.40 | 69.86 | 51.71 | 57.29 | 74.87 | 4.2 MainResults |     |     |     |     |     |     |
| ----------- | --- | ----- | ----- | ----- | ----- | ----- | --------------- | --- | --- | --- | --- | --- | --- |
| A-Mem       |     | 67.90 | 57.45 | 27.73 | 43.75 | 56.10 |                 |     |     |     |     |     |     |
MemoryOS 79.51 63.12 32.09 48.96 59.81 Superiority in Long-Context Reasoning. As
LightMem 82.76 68.09 50.16 52.08 71.36 showninTable1,FluxMemsetsanewstate-of-the-
FluxMem 96.19 91.49 89.72 87.50 93.44 artacrossallsub-categoriesontheLoCoMobench-
mark. WiththeGPT-4.1-minibackbone,FluxMem
| Table 1: | Evaluation | results | on      | LoCoMo   |     | benchmark. |          |                |     |         |     |     |          |
| -------- | ---------- | ------- | ------- | -------- | --- | ---------- | -------- | -------------- | --- | ------- | --- | --- | -------- |
|          |            |         |         |          |     |            | achieves | an outstanding |     | average |     | LMJ | score of |
| Bold and | underlined |         | entries | indicate | the | best and   |          |                |     |         |     |     |          |
95.06,significantlysurpassingFullContext(81.23)
second-bestresultswithineachgroup,respectively.
andthestrongestspecializedmemorysystemEv-
erMemOS(93.05).
Thisperformancegapiseven
the skills are validated as both highly useful and more pronounced when using Qwen3-30B-A3B-
concise,andtheofflineconsolidationends. 2507-Instruct backbone, where FluxMem main-
tainsahighaverageLMJof93.44,whilethenext
| 4 Experiments |     |     |     |     |     |     | bestbaselineFullContextdropsto74.87. |     |     |     |     |     |     |
| ------------- | --- | --- | --- | --- | --- | --- | ------------------------------------ | --- | --- | --- | --- | --- | --- |
4.1 ExperimentalSetup Robust Performance in Web Navigation. As
|          |     |            |     |          |     |          | shown      | in Table | 2, the       | evaluation |         | on Mind2Web |           |
| -------- | --- | ---------- | --- | -------- | --- | -------- | ---------- | -------- | ------------ | ---------- | ------- | ----------- | --------- |
| Datasets | &   | Baselines. | We  | evaluate |     | the pro- |            |          |              |            |         |             |           |
|          |     |            |     |          |     |          | highlights | the      | adaptability | of         | FluxMem |             | in noisy, |
posedframeworkacrossthreechallengingbench-
|        |        |           |     |     |      |            | real-worldwebenvironments. |        |     |         | Intherealisticset- |     |          |
| ------ | ------ | --------- | --- | --- | ---- | ---------- | -------------------------- | ------ | --- | ------- | ------------------ | --- | -------- |
| marks. | LoCoMo | (Maharana |     | et  | al., | 2024) pro- |                            |        |     |         |                    |     |          |
|        |        |           |     |     |      |            | ting without               | manual |     | element | filtering          | (   | ‡ ), our |
videsacomprehensiveevaluationforlong-context
frameworkdemonstratesconsistentimprovements
| reasoning,          | we        | compare     | FluxMem |            | against        | sev-    |                           |          |            |            |                   |      |        |
| ------------------- | --------- | ----------- | ------- | ---------- | -------------- | ------- | ------------------------- | -------- | ---------- | ---------- | ----------------- | ---- | ------ |
|                     |           |             |         |            |                |         | acrossbothbackbonemodels. |          |            |            | WithGPT-4.1-mini, |      |        |
| eral representative |           | baselines   |         | of         | conversational |         |                           |          |            |            |                   |      |        |
|                     |           |             |         |            |                |         | FluxMem                   | achieves | a          | Success    | Rate              | (SR) | of 8.1 |
| memory              | modeling: |             | ⃝1 Zep  | (Rasmussen |                | et al., |                           |          |            |            |                   |      |        |
|                     |           |             |         |            |                |         | in Cross-Task             |          | scenarios, | more       | than              | AWM  | base-  |
| 2025),              | ⃝2 Mem0   | (Chhikara   |         | et al.,    | 2025),         | ⃝3 A-   |                           |          |            |            |                   |      |        |
|                     |           |             |         |            |                |         | line (3.6).               | This     | trend      | is further | reinforced        |      | with   |
| Mem (Xu             | et        | al., 2025), | ⃝4      | MemoryOS   |                | (Kang   |                           |          |            |            |                   |      |        |
Gemini-2.5-flash,whereFluxMemreachesaneven
| et al., 2025),               |        | ⃝5 Nemori | (Nan      | et  | al.,       | 2025), ⃝6   |                |               |           |            |             |         |      |
| ---------------------------- | ------ | --------- | --------- | --- | ---------- | ----------- | -------------- | ------------- | --------- | ---------- | ----------- | ------- | ---- |
|                              |        |           |           |     |            |             | higher         | SR of         | 9.6 in    | Cross-Task | evaluation, |         | sub- |
| LightMem(Fangetal.,2025b),⃝7 |        |           |           |     | MIRIX(Wang |             |                |               |           |            |             |         |      |
|                              |        |           |           |     |            |             | stantially     | outperforming |           | AWM        | (5.6).      | Across  | all  |
| and Chen,                    | 2025), | and⃝8     | EverMemOS |     |            | (Hu et al., |                |               |           |            |             |         |      |
|                              |        |           |           |     |            |             | sub-categories |               | and model | backbones, |             | FluxMem |      |
2026a). Mind2Web(Dengetal.,2023)servesasa
consistentlyyieldshighestSSRandAF1scores.
testbedforwebnavigation,wecompareFluxMem
againstrepresentativebaselines: ⃝1 AWM(Wang State-of-the-ArtonGeneralistAssistantTasks.
et al., 2024c) and ⃝2 Reasoning Bank (Ouyang OnGAIAbenchmark,FluxMemdemonstratesex-
et al., 2025). For general assistant tasks, we em- ceptionalgainsoverthehigh-performanceFlash-
ploy GAIA (Mialon et al., 2023) to benchmark Searcher baseline and the meta-evolutionary sys-
against a wide array of frameworks: ⃝1 Ope- tem MemEvolve in Table 3. When utilizing Kimi
nAI Deep Research (OpenAI, 2024), ⃝2 Lang- K2,ourframeworkbooststheaveragesuccessrate
fun (Peng, 2023), ⃝3 Magnetic-1 (Fourney et al., from52.12to64.85,achievingaremarkableabso-
2024),⃝4 AgentKB(Tangetal.,2025b),⃝5 smo- luteimprovementof12.73%. Inhigh-complexity
lagents(Roucheretal.,2025),⃝6 Alita(Qiuetal., tasks (Level 3), FluxMem reaches a success rate

|     |     | Cross-Task |     | Cross-Website |     |     | Cross-Domain |     | AVG |     |
| --- | --- | ---------- | --- | ------------- | --- | --- | ------------ | --- | --- | --- |
Method
|     |     | EA AF1 | SSR SR | EA AF1 | SSR | SR EA | AF1 | SSR SR EA | AF1 SSR | SR  |
| --- | --- | ------ | ------ | ------ | --- | ----- | --- | --------- | ------- | --- |
GPT-4.1-mini
NoMemory‡
34.5 64.7 28.0 2.8 33.0 60.4 24.6 1.1 30.1 55.9 24.6 0.7 31.3 58.1 25.2 1.1
AWM‡
37.4 71.4 31.6 3.6 34.5 62.8 26.1 1.1 30.3 56.9 24.9 1.0 32.2 60.4 26.3 1.5
AWM† 64.6 82.3 56.3 9.1 62.9 79.7 52.7 4.5 50.5 69.3 43.9 2.0 54.8 73.1 47.4 3.7
FluxMem‡ 60.7 77.5 56.7 8.1 60.5 75.6 55.4 7.9 56.2 69.4 52.1 4.3 57.6 71.7 53.4 5.5
FluxMem† 70.4 84.2 60.1 13.5 70.2 82.1 58.7 9.2 65.2 75.3 55.3 7.2 66.8 77.9 56.6 8.6
Gemini-2.5-flash
NoMemory‡ 40.7 69.5 35.6 2.8 35.7 64.7 28.3 1.7 22.1 37.2 18.6 1.8 20.5 46.9 23.1 2.0
AWM‡ 53.1 76.6 48.0 5.6 48.9 71.5 44.3 3.4 41.6 60.2 38.1 1.5 44.7 64.8 40.8 2.5
AWM† 67.3 82.2 60.9 8.7 63.0 77.0 55.3 4.5 52.0 67.0 47.9 3.4 56.3 71.2 51.3 4.5
ReasoningBank† 52.1 60.4 44.9 4.8 44.3 52.6 33.9 3.3 40.6 41.3 36.6 1.6 43.2 46.4 37.8 2.4
FluxMem‡
61.6 77.4 57.0 9.6 59.4 72.8 56.1 7.5 58.5 70.1 55.9 5.0 59.2 71.8 56.1 6.2
FluxMem† 71.3 83.0 61.3 11.1 65.9 77.0 59.7 8.5 64.8 70.3 54.6 7.0 66.2 73.6 56.5 5.9
Table2: EvaluationresultsonMind2Web. †denotesthefilteredsettingwithmanualremovalofnon-goldenHTML
elements;‡denotestherealisticsettingwithoutanypre-filtering(seeAppendixA.2fordetails). Boldandunderline
denotethebestandsecond-bestresults.
| Framework |     | Model |     | Avg. |     | Level1 |     | Level2 | Level3 |     |
| --------- | --- | ----- | --- | ---- | --- | ------ | --- | ------ | ------ | --- |
Closed-sourceAgentFrameworks
| Langfun            |     | Claude3.7etc.   |     | 71.52 |     | 83.02 |     | 68.60 | 57.69 |     |
| ------------------ | --- | --------------- | --- | ----- | --- | ----- | --- | ----- | ----- | --- |
| OpenAIDeepResearch |     | OpenAIo1,o3etc. |     | 67.36 |     | 74.29 |     | 69.06 | 47.60 |     |
Open-SourceAgentFrameworks
| Magnetic-1     |     | OpenAIo1etc.             |     | 46.06 |     | 56.60 |     | 46.51 | 23.08 |     |
| -------------- | --- | ------------------------ | --- | ----- | --- | ----- | --- | ----- | ----- | --- |
| AgentKB        |     | GPT-4.1                  |     | 61.21 |     | 79.25 |     | 58.14 | 34.62 |     |
| Alita          |     | Claude-3.7-Sonnet,GPT-4o |     | 72.73 |     | 81.13 |     | 75.58 | 46.15 |     |
| Smolagents     |     | GPT-4.1                  |     | 55.15 |     | 67.92 |     | 53.49 | 34.62 |     |
| Smolagents     |     | GPT-5-mini               |     | 55.75 |     | 69.81 |     | 54.65 | 30.77 |     |
| Flash-Searcher |     | GPT-5-mini               |     | 69.09 |     | 79.25 |     | 69.77 | 46.15 |     |
| Flash-Searcher |     | KimiK2                   |     | 52.12 |     | 58.49 |     | 52.33 | 34.62 |     |
| Flash-Searcher |     | DeepSeekV3.2             |     | 60.61 |     | 79.25 |     | 53.49 | 46.15 |     |
MemEvolve GPT-5-mini 69.09→73.33↑4.24 79.25→83.02↑3.77 69.77→73.26↑3.49 46.15→53.85↑7.70
MemEvolve KimiK2 52.12→61.21↑9.09 58.49→67.92↑9.43 52.33→63.95↑11.62 34.62→38.46↑3.84
MemEvolve DeepSeekV3.2 60.61→67.88↑7.27 79.25→83.02↑3.77 53.49→63.95↑10.46 46.15→50.00↑3.85
FluxMem GPT-5-mini 69.09→76.36↑7.27 79.25→88.68↑9.43 69.77→75.58↑5.81 46.15→53.85↑7.70
FluxMem KimiK2 52.12→64.85↑12.73 58.49→77.36↑18.87 52.33→62.79↑10.46 34.62→46.15↑11.53
FluxMem DeepSeekV3.2 60.61→70.30↑9.69 79.25→81.13↑1.88 53.49→69.77↑16.28 46.15→50.00↑3.85
Table3: EvaluationresultsonGAIAbenchmark. Color-codedarrowsdenoteimprovementsrelativetotheFlash-
Searcherbaseline,withdeepergreenshadesindicatinglargerscoreimprovements. Boldandunderlineindicatethe
bestandsecond-bestfinalresultsacrossallmethods,respectively.
of53.85withGPT-5-mini,effectivelymatchingor isobservedwithQwen3-30B-A3B,wheretheaver-
exceeding the capabilities of much larger closed- agescorefallsfrom93.44%to84.74%upontheex-
sourceagentframeworks. clusionofStageII,whileothertwoablationsshow
|                   |     |     |     |     | relativelysmallerimpacts.                 |     |     | Inmemory-centricsce- |     |     |
| ----------------- | --- | --- | --- | --- | ----------------------------------------- | --- | --- | -------------------- | --- | --- |
| 4.3 AblationStudy |     |     |     |     | narioslikeLoCoMo,whereallrequiredevidence |     |     |                      |     |     |
canbedirectlyretrievedorsimplyinferredfromthe
| We conduct | ablation | studies | on LoCoMo | and |     |     |     |     |     |     |
| ---------- | -------- | ------- | --------- | --- | --- | --- | --- | --- | --- | --- |
Mind2Web to evaluate the contribution of three providedcontext,tasksrelymoreonaccuraterecall
|     |     |     |     |     | thancomplexreasoning. |     |     | Consequently,theStage |     |     |
| --- | --- | --- | --- | --- | --------------------- | --- | --- | --------------------- | --- | --- |
stages,asshowninFigure3(a),(b)and(c).
IIrefinementmechanism,whichexpandsretrieval
OnLoCoModataset,StageII(Feedback-Driven
orprunesirrelevantmemorynodes,yieldssubstan-
Refinement)provestobethemostcriticalcompo-
tialperformancegainsbyhelpingtheagentfindthe
| nent. For | GPT-4.1 | mini, removing | Stage | II leads |               |     |                                    |     |     |     |
| --------- | ------- | -------------- | ----- | -------- | ------------- | --- | ---------------------------------- | --- | --- | --- |
|           |         |                |       |          | correctfacts. |     | Insuchsettings,refiningthesemantic |     |     |     |
toasubstantialdecreaseintheaverageLMJscore,
knowledgelayerproveshighlyeffective,whilethe
| droppingfrom95.06%to85.32%. |     |     | Asimilartrend |     |     |     |     |     |     |     |
| --------------------------- | --- | --- | ------------- | --- | --- | --- | --- | --- | --- | --- |

Figure3: DetailedanalysisofFluxMemcomponentsandevolutiondynamics: (a)Ablationstudyofdifferentstages
onLoCoMousingGPT-4.1-mini. (b)AblationstudyofdifferentstagesonLoCoMousingQwen3-30B-A3B-2507-
Instrcut. (c)AblationstudyofdifferentstagesonMind2WebusingGPT-4.1-mini. (d)Performanceimprovement
acrosssub-tasksrelativetothenumberofrefinementroundsinStageII.(e)Modelaccuracytrendsandconvergence
oftheProcedureEvolutionMaturityScore(PEMS)acrossevolutionrounds.
proceduralskilllayercontributesrelativelyless. 4.5 AnalysisofMemoryEvolutionand
Convergence
Incontrast,ontheMind2Webdataset,StageIII
(Long-TermConsolidation)emergesastheprimary
|     |     |     |     |     |     |     | At this | point, | the sensitivity | threshold |     | ϵ can be |
| --- | --- | --- | --- | --- | --- | --- | ------- | ------ | --------------- | --------- | --- | -------- |
performancedriver. Forinstance,removingStage utilizedtoterminatetheevolutionprocess.
IIIforGPT-4.1-minicausesadrasticperformance AsshowninFigure3(e),ontheLoCoModataset,
drop(e.g.,thesuccessrateonthefirstsub-category
whileStageIIIprovidesaperformanceboost(from
| falls from | 8.1% | to 3.2%), |     | while the | impact | of re- |        |          |             |     |          |         |
| ---------- | ---- | --------- | --- | --------- | ------ | ------ | ------ | -------- | ----------- | --- | -------- | ------- |
|            |      |           |     |           |        |        | 91.16% | at round | 0 to 95.06% |     | at round | 5), the |
moving Stage II is relatively moderate. This dis- gainsaremoremoderatecomparedtoStageII.This
| parity suggests |     | that | for complex, | multi-step |     | web |             |     |             |      |                   |     |
| --------------- | --- | ---- | ------------ | ---------- | --- | --- | ----------- | --- | ----------- | ---- | ----------------- | --- |
|                 |     |      |              |            |     |     | aligns with | our | observation | that | for fact-oriented |     |
navigationtasksrequiringstrongreasoning,theex-
|          |           |     |           |          |       |     | tasks, the | primary   | role of    | Stage      | III is | to summa- |
| -------- | --------- | --- | --------- | -------- | ----- | --- | ---------- | --------- | ---------- | ---------- | ------ | --------- |
| traction | of skills | and | evolution | of skill | nodes | in  |            |           |            |            |        |           |
|          |           |     |           |          |       |     | rize and   | stabilize | background | knowledge. |        | More      |
StageIIIaremorevitalthanshort-termrefinement. importantly,weobserveaclearconvergencetrend
|     |     |     |     |     |     |     | in the PEMS |                                  | metric (scaled | by  | a factor | for visi- |
| --- | --- | --- | --- | --- | --- | --- | ----------- | -------------------------------- | -------------- | --- | -------- | --------- |
|     |     |     |     |     |     |     | bility).    | ThePEMSincreasesfrom0.072to0.158 |                |     |          |           |
4.4 AnalysisofIterativeRefinement
withinthefirstfourroundsandstabilizesat0.159
|            |     |        |     |            |     |         | by round | 5. This | convergence |     | indicates | that the |
| ---------- | --- | ------ | --- | ---------- | --- | ------- | -------- | ------- | ----------- | --- | --------- | -------- |
| We analyze | the | impact | of  | the number | of  | refine- |          |         |             |     |           |          |
memorymaturitymechanismeffectivelyidentifies
| ment iterations |     | in Stage | II  | on performance. |     | The |     |     |     |     |     |     |
| --------------- | --- | -------- | --- | --------------- | --- | --- | --- | --- | --- | --- | --- | --- |
whentheanchornodeshavereachedastablestate
numberofrefinementrounds(T)inStageIIserves
|               |     |         |         |             |      |     | ofknowledgerepresentation. |     |     | Atthispoint,thesen- |     |     |
| ------------- | --- | ------- | ------- | ----------- | ---- | --- | -------------------------- | --- | --- | ------------------- | --- | --- |
| as a critical |     | scaling | factor. | We evaluate | this | ef- |                            |     |     |                     |     |     |
sitivitythresholdϵcanbeutilizedtoterminatethe
| fectontheLoCoMobyvaryingT |           |       |     | from0to5,as         |     |     |              |          |                 |            |              |           |
| ------------------------- | --------- | ----- | --- | ------------------- | --- | --- | ------------ | -------- | --------------- | ---------- | ------------ | --------- |
|                           |           |       |     |                     |     |     | evolution    | process, | thereby         | preventing |              | redundant |
| shown                     | in Figure | 3(d). | The | results demonstrate |     | a   |              |          |                 |            |              |           |
|                           |           |       |     |                     |     |     | computations |          | once the memory |            | has captured | the       |
consistentandmonotonicimprovementacrossall
essentialtask-relatedinsights.
| sub-categories |         | and the   | overall | score.         | Without    | re-     |               |     |     |     |     |     |
| -------------- | ------- | --------- | ------- | -------------- | ---------- | ------- | ------------- | --- | --- | --- | --- | --- |
| finement       | (T      | = 0), the | agent   | achieves       | an average |         |               |     |     |     |     |     |
|                |         |           |         |                |            |         | 4.6 CaseStudy |     |     |     |     |     |
| score of       | 85.32%. | By        | T =     | 5, the average |            | perfor- |               |     |     |     |     |     |
mancereaches95.06%. Thissteadygainsuggests Figure4presentsaGAIAtabularreasoningtask,
thattherefinementmechanismallowstheagentto wheretheagentmustidentifythecountrywiththe
refineconnectionsandfindmoreusefulfactualevi- highestaveragemedalsperathletefromaCSVfile.
dences. Thediminishingreturnsobservedbetween FollowingStageI,FluxMeminitializesthework-
T = 4andT = 5(animprovementofonly0.54%) ing context S (q) by activating a local subgraph
0
indicatethattheagent’sperformancebeginstosat- containingsemanticknowledge(e.g.,CSVparsing
urateasitapproachestheoptimalevidencepath. andspreadsheetAPIs),arelevantepisodictrajec-

|     |     | Figure4: | CaseStudy. | Thekeypointshavebeenhighlightedinred. |     |     |     |     |
| --- | --- | -------- | ---------- | ------------------------------------- | --- | --- | --- | --- |
tory for tabular ranking, and a coarse procedural Self Evolving Agent Memory. Agent self-
skillforgenerictableQA.Thefirstexecutionstep evolution is typically driven by memory evolv-
succeeds, correctly parsing the file schema from ing(angGaoetal.,2026;Fangetal.,2025a;Shinn
environmentalobservationObs . et al.,2023), which canbe categorized into three
1
However,atthenextstep,theagentincorrectly paradigms. (i) Works such as Expel (Zhao et al.,
invokes a spreadsheet visualization API for ag- 2024), AWM (Wang et al., 2024c), and Reason-
gregation, which triggers an environmental fail- ingBank (Ouyang et al., 2025) maintain a con-
ure due to rendering limitations. FluxMem at- textual memory repository (Liu et al., 2025; Wei
tributes this failure to a connectivity mismatch etal.,2025;Caietal.,2025),distillingexperiences
andperformstargetedtopologicaledits: itprunes from historical trajectories to enhance agent ca-
theineffectivesemanticconnectionwhileexpand- pabilities (Qiu et al., 2025). These methods vary
ing connectivity toward a more suitable Python in the granularity of trajectory processing (Fang
data-analysisAPI,yieldingarefinedcontextS′(q).
|     |     |     |     |     | et al., 2026). | In addition | to successful | experi- |
| --- | --- | --- | --- | --- | -------------- | ----------- | ------------- | ------- |
1
Subsequently,althoughaggregationsucceeds,self- ences, someapproaches (Tang etal., 2025b; Cao
verification reveals that the inherited procedural et al., 2025) incorporate failure cases, while oth-
skillisoverlycoarse-grained: itsupportsranking ers(Wuetal.,2025)introduceiterativeevolution
existingstatisticsbutfailstocomposetherequired mechanisms. (ii)Otherworksfocusonparametric
metric (medals per athlete). This triggers Node memory. SEAL (Zweiger et al., 2025) explores
Reshape, replacing the skill with a finer-grained thepotentialofagentself-training,whileAgentE-
|     |     |     |     |     | volver (Zhai | et al., 2025) | and Agent0 | (Xia et al., |
| --- | --- | --- | --- | --- | ------------ | ------------- | ---------- | ------------ |
statisticalaggregationprocedure.
2025)concentrateondataacquisitionandreward
5 RelatedWork
|     |     |     |     |     | design. | The evolutionary | mechanisms | primarily |
| --- | --- | --- | --- | --- | ------- | ---------------- | ---------- | --------- |
includeSFT(Zhouetal.,2025),RL(Zhangetal.,
| HierarchicalStructuredMemorySystems. |     |     |     | Hi- |        |                     |      |                |
| ------------------------------------ | --- | --- | --- | --- | ------ | ------------------- | ---- | -------------- |
|                                      |     |     |     |     | 2026b) | and other paradigms | such | as early expe- |
erarchicalmemorysystemsorganizememoryunits
|         |          |             |            |       | rience (Shi | et al., 2025). | (iii) Some | works mod- |
| ------- | -------- | ----------- | ---------- | ----- | ----------- | -------------- | ---------- | ---------- |
| through | specific | topologies. | Tree-based | memo- |             |                |            |            |
ifymodelarchitecturestoenabledeepermemory-
riesabstractdataintohierarchicallevels(Aetal.,
|          |         |        |                   |        | augmented | evolving. | This is achieved | by either |
| -------- | ------- | ------ | ----------------- | ------ | --------- | --------- | ---------------- | --------- |
| 2024; Ye | et al., | 2025), | while graph-based | struc- |           |           |                  |           |
introducingadditionalparametersasexternalmem-
| tures offer | greater | connectivity | dynamics | (Long |     |     |     |     |
| ----------- | ------- | ------------ | -------- | ----- | --- | --- | --- | --- |
ory(Wangetal.,2024b,a)tomanageinformation
| etal.,2025). | Pyramidmechanismsconstructmulti- |     |     |     |     |     |     |     |
| ------------ | -------------------------------- | --- | --- | --- | --- | --- | --- | --- |
acquisitionandforgetting,orproposingnovelarchi-
levelabstractionstofacilitatecoarse-to-finequery-
tectures(Behrouzetal.,2024,2025a,b)toenhance
| ing(Hanetal.,2025;Rasmussenetal.,2025). |     |     |     | Al- |     |     |     |     |
| --------------------------------------- | --- | --- | --- | --- | --- | --- | --- | --- |
theinherentmemorycapacityofbasemodels.
| ternatively, | heterogeneous |      | multi-layer      | structures |     |     |     |     |
| ------------ | ------------- | ---- | ---------------- | ---------- | --- | --- | --- | --- |
| partition    | memory        | into | distinct modules | (Zhang     |     |     |     |     |
6 Conclusion
etal.,2025b;Xuetal.,2026)orlevelsspecialized
forspecificinformationtypesorfunctions(Zhang WeintroducedFluxMem,anevolutionaryframe-
etal.,2025a;Gutiérrezetal.,2025a,b). work conceptualizing agent memory as dy-

namic connectivity. By a three-phase evolution, andintegrityofthework.
| FluxMem    | enables |     | autonomous |         | memory | adapta-  |     |     |     |     |     |
| ---------- | ------- | --- | ---------- | ------- | ------ | -------- | --- | --- | --- | --- | --- |
| tion. SOTA | results |     | across     | LoCoMo, |        | Mind2Web |     |     |     |     |     |
References
| and GAIA, | provides |     | a principled |     | foundation | for |     |     |     |     |     |
| --------- | -------- | --- | ------------ | --- | ---------- | --- | --- | --- | --- | --- | --- |
self-evolvingagentsindynamicenvironments.
AadharshAadhithyaA,SachinKumarS,andSomanK.
|             |     |     |     |     |     |     | P.2024.                                         | Enhancinglong-termmemoryusinghierar- |     |     |     |
| ----------- | --- | --- | --- | --- | --- | --- | ----------------------------------------------- | ------------------------------------ | --- | --- | --- |
| Limitations |     |     |     |     |     |     | chicalaggregatetreeforretrievalaugmentedgenera- |                                      |     |     |     |
tion. Preprint,arXiv:2406.06124.
| Despite | the demonstrated |     |     | effectiveness, |     | several |     |     |     |     |     |
| ------- | ---------------- | --- | --- | -------------- | --- | ------- | --- | --- | --- | --- | --- |
HuanangGao,JiayiGeng,WenyueHua,MengkangHu,
limitations in our experimental design warrant Xinzhe Juan, Hongzhang Liu, Shilong Liu, Jiahao
| acknowledgment: |     | Computational |     |     | Overhead | of  |     |     |     |     |     |
| --------------- | --- | ------------- | --- | --- | -------- | --- | --- | --- | --- | --- | --- |
Qiu,XuanQi,YiranWu,HongruWang,HanXiao,
Closed-LoopOperations. StagesIIandIIIrelyon YuhangZhou,ShaokunZhang,JiayiZhang,JinyuXi-
ang,YixiongFang,QiwenZhao,DongruiLiu,and8
| iterativeLLMcallsforcontextverification, |     |     |     |     |     | topo- |              |     |                                    |     |     |
| ---------------------------------------- | --- | --- | --- | --- | --- | ----- | ------------ | --- | ---------------------------------- | --- | --- |
|                                          |     |     |     |     |     |       | others.2026. |     | Asurveyofself-evolvingagents:What, |     |     |
logical editing, and skill induction. Our current when,how,andwheretoevolveonthepathtoartifi-
evaluationprioritizestasksuccessandconvergence, Preprint,arXiv:2507.21046.
cialsuperintelligence.
butdoesnotsystematicallymeasuretheassociated
|              |     |           |          |                         |     |       | AliBehrouz, | MeisamRazaviyayn, |        | PeilinZhong,        | and |
| ------------ | --- | --------- | -------- | ----------------------- | --- | ----- | ----------- | ----------------- | ------ | ------------------- | --- |
| latency,     | API | cost,     | or token | consumption,            |     | which |             |                   |        |                     |     |
|              |     |           |          |                         |     |       | Vahab       | Mirrokni.         | 2025a. | It’s all connected: | A   |
| are critical | for | real-time |          | or resource-constrained |     |       |             |                   |        |                     |     |
journeythroughtest-timememorization,attentional
deployments. Static Benchmark Protocols. Ex- bias, retention, and online optimization. Preprint,
arXiv:2504.13173.
| periments | are | conducted |     | on pre-collected, |     | static |     |     |     |     |     |
| --------- | --- | --------- | --- | ----------------- | --- | ------ | --- | --- | --- | --- | --- |
datasets(LoCoMo,Mind2Web,GAIA).Whiledi-
|     |     |     |     |     |     |     | AliBehrouz, | MeisamRazaviyayn, |     | PeilinZhong, | and |
| --- | --- | --- | --- | --- | --- | --- | ----------- | ----------------- | --- | ------------ | --- |
verse,thesebenchmarksdonotfullysimulatecon- Vahab Mirrokni. 2025b. Nested learning: The il-
tinuous, open-world distribution shifts or stream- lusion of deep learning architectures. Preprint,
arXiv:2512.24695.
ingenvironmentswheretaskboundariesblurand
| memory | decay | must | be actively |     | managed | along- |     |     |     |     |     |
| ------ | ----- | ---- | ----------- | --- | ------- | ------ | --- | --- | --- | --- | --- |
AliBehrouz,PeilinZhong,andVahabMirrokni.2024.
sideevolution. HyperparameterSensitivity. The Titans: Learningtomemorizeattesttime. Preprint,
arXiv:2501.00663.
| framework         | introduces |        | several | control |             | thresholds |     |     |     |     |     |
| ----------------- | ---------- | ------ | ------- | ------- | ----------- | ---------- | --- | --- | --- | --- | --- |
| (e.g., refinement |            | rounds |         | T, PEMS | convergence |            |     |     |     |     |     |
ZhichengCai,XinyuanGuo,YuPei,JiangtaoFeng,Jin-
thresholdϵ,retrievaltop-k). Ourablationsfocuson songSu,JiangjieChen,Ya-QinZhang,Wei-YingMa,
componentefficacybutlackacomprehensivesen- MingxuanWang,andHaoZhou.2025. Flex: Con-
|     |     |     |     |     |     |     | tinuous | agent | evolution | via forward learning | from |
| --- | --- | --- | --- | --- | --- | --- | ------- | ----- | --------- | -------------------- | ---- |
sitivityanalysisacrossdifferentmodelbackbones
|            |               |     |     |          |        |      | experience. | Preprint,arXiv:2511.06449. |     |     |     |
| ---------- | ------------- | --- | --- | -------- | ------ | ---- | ----------- | -------------------------- | --- | --- | --- |
| and highly | heterogeneous |     |     | domains. | Future | work |             |                            |     |     |     |
should systematically evaluate the robustness of Zouying Cao, Jiaji Deng, Li Yu, Weikang Zhou,
|     |     |     |     |     |     |     | ZhaoyangLiu,BolinDing,andHaiZhao.2025. |     |     |     | Re- |
| --- | --- | --- | --- | --- | --- | --- | -------------------------------------- | --- | --- | --- | --- |
theseparametersundervaryingcomputationalbud-
|               |     |               |     |             |     |       | memberme,refineme: |     | Adynamicproceduralmem- |     |     |
| ------------- | --- | ------------- | --- | ----------- | --- | ----- | ------------------ | --- | ---------------------- | --- | --- |
| gets. Offline |     | Consolidation |     | Scheduling. |     | Stage |                    |     |                        |     |     |
oryframeworkforexperience-drivenagentevolution.
| IIIisexecutedofflineinperiodicbatches. |     |     |     |     |     | Thecur- |     |     |     |     |     |
| -------------------------------------- | --- | --- | --- | --- | --- | ------- | --- | --- | --- | --- | --- |
Preprint,arXiv:2512.10696.
rentexperimentalsetupdoesnotevaluatedynamic
|     |     |     |     |     |     |     | Ding Chen, | Simin | Niu, Kehang | Li, Peng | Liu, Xiang- |
| --- | --- | --- | --- | --- | --- | --- | ---------- | ----- | ----------- | -------- | ----------- |
schedulingstrategiesorthetrade-offbetweencon-
pingZheng,BoTang,XinchiLi,FeiyuXiong,and
solidationfrequencyandonlineperformancedegra-
|     |     |     |     |     |     |     | Zhiyu | Li. 2026a. | Halumem: | Evaluating | halluci- |
| --- | --- | --- | --- | --- | --- | --- | ----- | ---------- | -------- | ---------- | -------- |
dation, which are essential for practical lifelong nations in memory systems of agents. Preprint,
arXiv:2511.03506.
agentdeployment.
YiningChen,JihaoZhao,BoTang,HaofenWang,Yue
UseofAIAssistants
Zhang,FeiHuang,FeiyuXiong,andZhiyuLi.2026b.
|     |     |     |     |     |     |     | Memprivacy: |     | Privacy-preservingpersonalizedmem- |     |     |
| --- | --- | --- | --- | --- | --- | --- | ----------- | --- | ---------------------------------- | --- | --- |
Duringthepreparationofthismanuscript,AIlan-
|                                               |     |         |     |             |     |           | ory management    |     | for edge-cloud | agents. | Preprint, |
| --------------------------------------------- | --- | ------- | --- | ----------- | --- | --------- | ----------------- | --- | -------------- | ------- | --------- |
| guagemodelswereutilizedexclusivelyforlinguis- |     |         |     |             |     |           | arXiv:2605.09530. |     |                |         |           |
| tic refinement,                               |     | grammar |     | correction, | and | stylistic |                   |     |                |         |           |
PrateekChhikara,DevKhant,SaketAryan,Taranjeet
| polishing. | Thecoreresearchconcepts,experimen- |     |     |     |     |     |                             |     |     |       |          |
| ---------- | ---------------------------------- | --- | --- | --- | --- | --- | --------------------------- | --- | --- | ----- | -------- |
|            |                                    |     |     |     |     |     | Singh,andDeshrajYadav.2025. |     |     | Mem0: | Building |
tal design, methodological implementation, nar- production-readyaiagentswithscalablelong-term
rative structure, and all figures/illustrations were memory. Preprint,arXiv:2504.19413.
independentlyconceived,developed,andverified
XiangDeng,YuGu,BoyuanZheng,ShijieChen,Sam
| by the | human | authors. | The | authors | retain | full re- |     |     |     |     |     |
| ------ | ----- | -------- | --- | ------- | ------ | -------- | --- | --- | --- | --- | --- |
Stevens,BoshiWang,HuanSun,andYuSu.2023.
sponsibilityforthescientificaccuracy,originality, Mind2web: Towardsageneralistagentfortheweb.

AdvancesinNeuralInformationProcessingSystems, YuyangHu,ShichunLiu,YanweiYue,GuibinZhang,
| 36:28091–28114. |     |     |     |     |     |     | BoyangLiu,FangyiZhu,JiahangLin,HonglinGuo, |     |     |     |     |     |
| --------------- | --- | --- | --- | --- | --- | --- | ------------------------------------------ | --- | --- | --- | --- | --- |
ShihanDou,ZhihengXi,SenjieJin,JiejunTan,Yan-
JinyuanFang,YanwenPeng,XiZhang,YingxuWang, bin Yin, Jiongnan Liu, Zeyu Zhang, Zhongxiang
XinhaoYi,GuibinZhang,YiXu,BinWu,SiweiLiu, Sun,YutaoZhu,HaoSun,BociPeng,and28others.
Zihao Li, Zhaochun Ren, Nikos Aletras, Xi Wang, 2026b. Memory in the age of ai agents. Preprint,
| Han Zhou, | and    | Zaiqiao          | Meng. | 2025a. | A       | compre- | arXiv:2512.13564. |     |     |     |     |     |
| --------- | ------ | ---------------- | ----- | ------ | ------- | ------- | ----------------- | --- | --- | --- | --- | --- |
| hensive   | survey | of self-evolving |       | ai     | agents: | A new   |                   |     |     |     |     |     |
paradigmbridgingfoundationmodelsandlifelong BowenJiang,YuanYuan,MaohaoShen,ZhuoqunHao,
Preprint,arXiv:2508.07407. ZhangchenXu,ZichenChen,ZiyiLiu,AnveshRao
agenticsystems.
Vijjini,JiashuHe,HanchaoYu,RadhaPoovendran,
Jizhan Fang, Xinle Deng, Haoming Xu, Ziyan Jiang, GregoryWornell,LyleUngar,DanRoth,SihaoChen,
Yuqi Tang, Ziwen Xu, Shumin Deng, Yunzhi and Camillo Jose Taylor. 2025. Personamem-v2:
Yao, Mengru Wang, Shuofei Qiao, and 1 oth- Towards personalized intelligence via learning im-
|             |     |           |             |     |     |           | plicituserpersonasandagenticmemory. |     |     |     |     | Preprint, |
| ----------- | --- | --------- | ----------- | --- | --- | --------- | ----------------------------------- | --- | --- | --- | --- | --------- |
| ers. 2025b. |     | Lightmem: | Lightweight |     | and | efficient |                                     |     |     |     |     |           |
arXiv:2512.06688.
| memory-augmented |     |     | generation. |     | arXiv | preprint |     |     |     |     |     |     |
| ---------------- | --- | --- | ----------- | --- | ----- | -------- | --- | --- | --- | --- | --- | --- |
arXiv:2510.18866.
|     |     |     |     |     |     |     | Jiazheng  | Kang, | Mingming           | Ji, | Zhe Zhao,     | and Ting |
| --- | --- | --- | --- | --- | --- | --- | --------- | ----- | ------------------ | --- | ------------- | -------- |
|     |     |     |     |     |     |     | Bai.2025. |       | Memoryosofaiagent. |     | arXivpreprint |          |
RunnanFang,YuanLiang,XiaobinWang,JialongWu,
| ShuofeiQiao,PengjunXie,FeiHuang,HuajunChen, |     |     |                            |       |                |     | arXiv:2506.06326. |       |     |               |       |       |
| ------------------------------------------- | --- | --- | -------------------------- | ----- | -------------- | --- | ----------------- | ----- | --- | ------------- | ----- | ----- |
| andNingyuZhang.2026.                        |     |     |                            | Memp: | Exploringagent |     |                   |       |     |               |       |       |
|                                             |     |     |                            |       |                |     | AM Clare          | Kelly | and | Hugh Garavan. | 2005. | Human |
| proceduralmemory.                           |     |     | Preprint,arXiv:2508.06433. |       |                |     |                   |       |     |               |       |       |
functionalneuroimagingofbrainchangesassociated
|               |     |       |         |         |     |           | withpractice. |     | Cerebralcortex,15(8):1089–1102. |     |     |     |
| ------------- | --- | ----- | ------- | ------- | --- | --------- | ------------- | --- | ------------------------------- | --- | --- | --- |
| Adam Fourney, |     | Gagan | Bansal, | Hussein |     | Mozannar, |               |     |                                 |     |     |     |
ChengTan,EduardoSalinas,Erkang,Zhu,Friederike
|     |     |     |     |     |     |     | Yitao Liu, | Chenglei |     | Si, Karthik | Narasimhan, | and |
| --- | --- | --- | --- | --- | --- | --- | ---------- | -------- | --- | ----------- | ----------- | --- |
Niedtner, GraceProebsting, GriffinBassman, Jack Shunyu Yao. 2025. Contextual experience replay
Gerrits, Jacob Alber, Peter Chang, Ricky Loynd, forself-improvementoflanguageagents. Preprint,
RobertWest,VictorDibia,AhmedAwadallah,Ece
arXiv:2506.06698.
| Kamar,        | Rafah | Hosn,                           | and Saleema |     | Amershi. | 2024. |           |        |     |            |        |           |
| ------------- | ----- | ------------------------------- | ----------- | --- | -------- | ----- | --------- | ------ | --- | ---------- | ------ | --------- |
| Magentic-one: |       | Ageneralistmulti-agentsystemfor |             |     |          |       |           |        |     |            |        |           |
|               |       |                                 |             |     |          |       | Lin Long, | Yichen | He, | Wentao Ye, | Yiyuan | Pan, Yuan |
solvingcomplextasks. Preprint,arXiv:2411.04468. Lin,HangLi,JunboZhao,andWeiLi.2025. See-
|     |     |     |     |     |     |     | ing,listening,remembering,andreasoning: |     |     |     |     | Amul- |
| --- | --- | --- | --- | --- | --- | --- | --------------------------------------- | --- | --- | --- | --- | ----- |
Paul W Frankland and Bruno Bontempi. 2005. The timodal agent with long-term memory. Preprint,
| organizationofrecentandremotememories. |     |     |     |     |     | Nature | arXiv:2508.09736. |     |     |     |     |     |
| -------------------------------------- | --- | --- | --- | --- | --- | ------ | ----------------- | --- | --- | --- | --- | --- |
reviewsneuroscience,6(2):119–130.
|     |     |     |     |     |     |     | Adyasha | Maharana, | Dong-Ho | Lee, | Sergey | Tulyakov, |
| --- | --- | --- | --- | --- | --- | --- | ------- | --------- | ------- | ---- | ------ | --------- |
BernalJiménezGutiérrez,YihengShu,YuGu,Michi- Mohit Bansal, Francesco Barbieri, and Yuwei
hiroYasunaga,andYuSu.2025a. Hipporag: Neu- Fang. 2024. Evaluating very long-term conver-
robiologicallyinspiredlong-termmemoryforlarge sational memory of llm agents. arXiv preprint
| languagemodels. |     | Preprint,arXiv:2405.14831. |     |     |     |     | arXiv:2402.17753. |     |     |     |     |     |
| --------------- | --- | -------------------------- | --- | --- | --- | --- | ----------------- | --- | --- | --- | --- | --- |
LingruiMei,JiayuYao,YuyaoGe,YiweiWang,Bao-
| Bernal Jiménez |     | Gutiérrez, | Yiheng |     | Shu, Weijian | Qi, |     |     |     |     |     |     |
| -------------- | --- | ---------- | ------ | --- | ------------ | --- | --- | --- | --- | --- | --- | --- |
longBi,YujunCai,JiazhiLiu,MingyuLi,Zhong-Zhi
| SizheZhou,andYuSu.2025b. |     |     |     | Fromragtomemory: |     |     |     |     |     |     |     |     |
| ------------------------ | --- | --- | --- | ---------------- | --- | --- | --- | --- | --- | --- | --- | --- |
Non-parametriccontinuallearningforlargelanguage Li,DuzhenZhang,ChenlinZhou,JiayiMao,Tianze
models. Preprint,arXiv:2502.14802. Xia, JiafengGuo, andShenghuaLiu.2025. Asur-
veyofcontextengineeringforlargelanguagemodels.
Preprint,arXiv:2507.13334.
| Haoyu Han, | Yu  | Wang, | Harry | Shomer, | Kai | Guo, Ji- |     |     |     |     |     |     |
| ---------- | --- | ----- | ----- | ------- | --- | -------- | --- | --- | --- | --- | --- | --- |
ayuanDing,YongjiaLei,MahanteshHalappanavar,
GrégoireMialon,ClémentineFourrier,ThomasWolf,
| Ryan      | A. Rossi,   | Subhabrata          |              | Mukherjee, |            | Xianfeng |                                  |     |                        |     |              |             |
| --------- | ----------- | ------------------- | ------------ | ---------- | ---------- | -------- | -------------------------------- | --- | ---------------------- | --- | ------------ | ----------- |
|           |             |                     |              |            |            |          | YannLeCun,                       |     | andThomasScialom.2023. |     |              | Gaia: a     |
| Tang,     | Qi He,      | Zhigang             | Hua,         | Bo Long,   | Tong       | Zhao,    |                                  |     |                        |     |              |             |
|           |             |                     |              |            |            |          | benchmarkforgeneralaiassistants. |     |                        |     | InTheTwelfth |             |
| NeilShah, | AminJavari, |                     | YinglongXia, |            | andJiliang |          |                                  |     |                        |     |              |             |
|           |             |                     |              |            |            |          | International                    |     | Conference             | on  | Learning     | Representa- |
| Tang.     | 2025.       | Retrieval-augmented |              |            | generation | with     |                                  |     |                        |     |              |             |
tions.
| graphs(graphrag). |                      | Preprint,arXiv:2501.00309. |     |                  |            |        |                   |              |              |                 |       |            |
| ----------------- | -------------------- | -------------------------- | --- | ---------------- | ---------- | ------ | ----------------- | ------------ | ------------ | --------------- | ----- | ---------- |
|                   |                      |                            |     |                  |            |        | Jiayan            | Nan, Wenquan |              | Ma, Wenlong     | Wu,   | and Yize   |
| Donald Olding     |                      | Hebb. 2005.                |     | The organization |            | of be- |                   |              |              |                 |       |            |
|                   |                      |                            |     |                  |            |        | Chen.             | 2025.        | Nemori:      | Self-organizing |       | agent mem- |
| havior:           | A neuropsychological |                            |     | theory.          | Psychology |        |                   |              |              |                 |       |            |
|                   |                      |                            |     |                  |            |        | ory inspired      |              | by cognitive | science.        | arXiv | preprint   |
| press.            |                      |                            |     |                  |            |        | arXiv:2508.03341. |              |              |                 |       |            |
Chuanrui Hu, Xingze Gao, Zuyi Zhou, Dannong Xu, OpenAI.2024. deepresearch.
| Yi Bai, | Xintong | Li, | Hui Zhang, |     | Tong Li, | Chong |     |     |     |     |     |     |
| ------- | ------- | --- | ---------- | --- | -------- | ----- | --- | --- | --- | --- | --- | --- |
Zhang, Lidong Bing, and 1 others. 2026a. Ever- Siru Ouyang, Jun Yan, I-Hung Hsu, Yanfei Chen,
memos: Aself-organizingmemoryoperatingsystem Ke Jiang, Zifeng Wang, Rujun Han, Long T. Le,
forstructuredlong-horizonreasoning. arXivpreprint SamiraDaruki,XiangruTang,VishyTirumalashetty,
| arXiv:2601.02163. |     |     |     |     |     |     | GeorgeLee,MahsanRofouei,HangfeiLin,Jiawei |     |     |     |     |     |
| ----------------- | --- | --- | --- | --- | --- | --- | ----------------------------------------- | --- | --- | --- | --- | --- |

Han,Chen-YuLee,andTomasPfister.2025. Reason- Chapter of the Association for Computational Lin-
ingbank: Scalingagentself-evolvingwithreasoning guistics(Volume1: LongPapers),pages7080–7106,
memory. Preprint,arXiv:2509.25140. Rabat,Morocco.AssociationforComputationalLin-
guistics.
CharlesPacker,SarahWooders,KevinLin,VivianFang,
|     |     |     |     |     |     | XiangruTang, | TianyuHu, | MuyangYe, |     | YanjunShao, |
| --- | --- | --- | --- | --- | --- | ------------ | --------- | --------- | --- | ----------- |
ShishirG.Patil,IonStoica,andJosephE.Gonzalez.
2024. Memgpt: Towardsllmsasoperatingsystems. Xunjian Yin, Siru Ouyang, Wangchunshu Zhou,
Preprint,arXiv:2310.08560. PanLu,ZhuoshengZhang,YilunZhao,ArmanCo-
|     |     |     |     |     |     | han, and | Mark Gerstein. | 2025a. | Chemagent: | Self- |
| --- | --- | --- | --- | --- | --- | -------- | -------------- | ------ | ---------- | ----- |
DaiyiPeng.2023. Langfun. updatinglibraryinlargelanguagemodelsimproves
|            |         |           |     |           |        | chemicalreasoning. | Preprint,arXiv:2501.06590. |     |     |     |
| ---------- | ------- | --------- | --- | --------- | ------ | ------------------ | -------------------------- | --- | --- | --- |
| Shihao Qi, | Jie Ma, | Rui Xing, | Wei | Guo, Xiao | Huang, |                    |                            |     |     |     |
ZhitaoGao,JianhaoDeng,JunLiu,LinglingZhang, XiangruTang,TianruiQin,TianhaoPeng,ZiyangZhou,
DanielShao,TingtingDu,XinmingWei,PengXia,
| Bifan Wei, | Boqian | Yang, | Pinghui | Wang, | Jianwen |     |     |     |     |     |
| ---------- | ------ | ----- | ------- | ----- | ------- | --- | --- | --- | --- | --- |
Sun, Jing Tao, Yaqiang Wu, Hui Liu, Yu Yao, and FangWu,HeZhu,GeZhang,JiahengLiu,Xingyao
TongliangLiu.2026. Beyondindividualintelligence: Wang, Sirui Hong, Chenglin Wu, Hao Cheng, Chi
Surveyingcollaboration,failureattribution,andself- Wang, and Wangchunshu Zhou. 2025b. Agent kb:
evolutioninllm-basedmulti-agentsystems. Preprint, Leveragingcross-domainexperienceforagenticprob-
|     |     |     |     |     |     | lemsolving. | Preprint,arXiv:2507.06229. |     |     |     |
| --- | --- | --- | --- | --- | --- | ----------- | -------------------------- | --- | --- | --- |
arXiv:2605.14892.
ChenxiWang,ZhuoyunYu,XinXie,WuguannanYao,
TianruiQin,QianbenChen,SinuoWang,HeXing,King
Zhu,HeZhu,DingfengShi,XinxinLiu,GeZhang, Runnan Fang, Shuofei Qiao, Kexin Cao, Guozhou
JiahengLiu,YuchenEleanorJiang,XitongGao,and Zheng, Xiang Qi, Peng Zhang, and Shumin Deng.
WangchunshuZhou.2025. Flash-searcher: Fastand 2026. Skillx:Automaticallyconstructingskillknowl-
|     |     |     |     |     |     | edgebasesforagents. |     | Preprint,arXiv:2604.04804. |     |     |
| --- | --- | --- | --- | --- | --- | ------------------- | --- | -------------------------- | --- | --- |
effectivewebagentsviadag-basedparallelexecution.
Preprint,arXiv:2509.25301.
PengWang,ZexiLi,NingyuZhang,ZiwenXu,Yunzhi
Yao,YongJiang,PengjunXie,FeiHuang,andHua-
JiahaoQiu,XuanQi,TongchengZhang,XinzheJuan,
|     |     |     |     |     |     | junChen.2024a. | Wise: | Rethinkingtheknowledge |     |     |
| --- | --- | --- | --- | --- | --- | -------------- | ----- | ---------------------- | --- | --- |
JiachengGuo,YifuLu,YiminWang,ZixinYao,Qi-
hanRen,XunJiang,XingZhou,DongruiLiu,Ling memoryforlifelongmodeleditingoflargelanguage
|     |     |     |     |     |     | models. | AdvancesinNeuralInformationProcessing |     |     |     |
| --- | --- | --- | --- | --- | --- | ------- | ------------------------------------- | --- | --- | --- |
Yang,YueWu,KaixuanHuang,ShilongLiu,Hongru
Systems,37:53764–53797.
| Wang,     | and Mengdi    | Wang.    | 2025.   | Alita:          | General- |                       |               |         |                 |          |
| --------- | ------------- | -------- | ------- | --------------- | -------- | --------------------- | ------------- | ------- | --------------- | -------- |
| ist agent | enabling      | scalable | agentic | reasoning       | with     |                       |               |         |                 |          |
|           |               |          |         |                 |          | YuWangandXiChen.2025. |               | Mirix:  | Multi-agentmem- |          |
| minimal   | predefinition | and      | maximal | self-evolution. |          |                       |               |         |                 |          |
|           |               |          |         |                 |          | ory system            | for llm-based | agents. | arXiv           | preprint |
Preprint,arXiv:2505.20286.
arXiv:2507.07957.
PrestonRasmussen,PavloPaliychuk,TravisBeauvais,
|                                |     |     |     |      |         | Yu Wang, | Yifan Gao, Xiusi | Chen, | Haoming | Jiang,     |
| ------------------------------ | --- | --- | --- | ---- | ------- | -------- | ---------------- | ----- | ------- | ---------- |
| JackRyan,andDanielChalef.2025. |     |     |     | Zep: | Atempo- |          |                  |       |         |            |
|                                |     |     |     |      |         | Shiyang  | Li, Jingfeng     | Yang, | Qingyu  | Yin, Zheng |
ralknowledgegrapharchitectureforagentmemory.
|     |     |     |     |     |     | Li, Xian | Li, Bing Yin, | Jingbo | Shang, | and Ju- |
| --- | --- | --- | --- | --- | --- | -------- | ------------- | ------ | ------ | ------- |
Preprint,arXiv:2501.13956.
|     |     |     |     |     |     | lian McAuley.  | 2024b.         | Memoryllm: |         | Towards   |
| --- | --- | --- | --- | --- | --- | -------------- | -------------- | ---------- | ------- | --------- |
|     |     |     |     |     |     | self-updatable | large language |            | models. | Preprint, |
AymericRoucher,AlbertVillanovadelMoral,Thomas
arXiv:2402.04624.
| Wolf, Leandro |     | von Werra, | and | Erik Kaunismäki. |     |     |     |     |     |     |
| ------------- | --- | ---------- | --- | ---------------- | --- | --- | --- | --- | --- | --- |
2025. ‘smolagents‘: a smol library to build Zora Zhiruo Wang, Jiayuan Mao, Daniel Fried, and
great agentic systems. https://github.com/ Graham Neubig. 2024c. Agent workflow memory.
huggingface/smolagents.
arXivpreprintarXiv:2409.07429.
YuchenShi,YuzhengCai,SiqiCai,ZihanXu,Lichao
|     |     |     |     |     |     | Tianxin Wei, | Noveen Sachdeva, |     | Benjamin | Coleman, |
| --- | --- | --- | --- | --- | --- | ------------ | ---------------- | --- | -------- | -------- |
Chen,YuleiQin,ZhijianZhou,XiangFei,Chaofan
ZhankuiHe,YuanchenBei,XuyingNing,Mengting
Qiu, Xiaoyu Tan, Gang Li, Zongyi Li, Haojia Lin, Ai, Yunzhe Li, Jingrui He, Ed H. Chi, Chi Wang,
GuocanCai,YongMao,YunshengWu,KeLi,and Shuo Chen, Fernando Pereira, Wang-Cheng Kang,
XingSun.2025. Youtu-agent: Scalingagentproduc- and Derek Zhiyuan Cheng. 2025. Evo-memory:
tivitywithautomatedgenerationandhybridpolicy
Benchmarkingllmagenttest-timelearningwithself-
| optimization. | Preprint,arXiv:2512.24615. |          |     |        |           |                 |                            |     |     |     |
| ------------- | -------------------------- | -------- | --- | ------ | --------- | --------------- | -------------------------- | --- | --- | --- |
|               |                            |          |     |        |           | evolvingmemory. | Preprint,arXiv:2511.20857. |     |     |     |
| Noah Shinn,   | Federico                   | Cassano, |     | Ashwin | Gopinath, |                 |                            |     |     |     |
RongWu,XiaomanWang,JianbiaoMei,PinlongCai,
Karthik Narasimhan, and Shunyu Yao. 2023. Re- Daocheng Fu, Cheng Yang, Licheng Wen, Xue-
flexion: Languageagentswithverbalreinforcement meng Yang, Yufan Shen, Yuxin Wang, and Bo-
learning. AdvancesinNeuralInformationProcess- tian Shi. 2025. Evolver: Self-evolving llm agents
ingSystems,36:8634–8652. through an experience-driven lifecycle. Preprint,
arXiv:2510.16079.
| Mirac Suzgun, | Mert | Yuksekgonul, |     | Federico | Bianchi, |     |     |     |     |     |
| ------------- | ---- | ------------ | --- | -------- | -------- | --- | --- | --- | --- | --- |
DanJurafsky,andJamesZou.2026. Dynamiccheat- PengXia, KaideZeng, JiaqiLiu, CanQin, FangWu,
sheet: Test-timelearningwithadaptivememory. In Yiyang Zhou, Caiming Xiong, and Huaxiu Yao.
Proceedingsofthe19thConferenceoftheEuropean 2025. Agent0: Unleashingself-evolvingagentsfrom

zero data via tool-integrated reasoning. Preprint, Andrew Zhao, Daniel Huang, Quentin Xu, Matthieu
arXiv:2511.16043. Lin, Yong-Jin Liu, and Gao Huang. 2024. Expel:
|     |     |     |     |     |     |     | Llmagentsareexperientiallearners. |     |     |     |     | InProceedings |     |
| --- | --- | --- | --- | --- | --- | --- | --------------------------------- | --- | --- | --- | --- | ------------- | --- |
BuqiangXu,YijunChen,JizhanFang,RuobinZhong, of the AAAI Conference on Artificial Intelligence,
YunzhiYao,YuqiZhu,LunDu,andShuminDeng.
volume38,pages19632–19642.
| 2026. | Structmem: | Structured |     | memory | for | long- |     |     |     |     |     |     |     |
| ----- | ---------- | ---------- | --- | ------ | --- | ----- | --- | --- | --- | --- | --- | --- | --- |
horizonbehaviorinllms. CoRR,abs/2604.21748. Huichi Zhou, Yihang Chen, Siyuan Guo, Xue Yan,
|     |     |     |     |     |     |     | Kin Hei | Lee, | Zihan | Wang, | Ka  | Yiu Lee, | Guchun |
| --- | --- | --- | --- | --- | --- | --- | ------- | ---- | ----- | ----- | --- | -------- | ------ |
Wujiang Xu, Kai Mei, Hang Gao, Juntao Tan, Zu- Zhang,KunShao,LinyiYang,andJunWang.2025.
jie Liang, and Yongfeng Zhang. 2025. A-mem: Memento:Fine-tuningllmagentswithoutfine-tuning
Agentic memory for llm agents. arXiv preprint llms. Preprint,arXiv:2508.16153.
arXiv:2502.12110.
AdamZweiger,JyothishPari,HanGuo,EkinAkyürek,
KeYang,ZixiChen,XuanHe,JizeJiang,MichelGalley,
|                      |       |          |          |                |           |     | YoonKim,andPulkitAgrawal.2025. |     |                            |     |     | Self-adapting |     |
| -------------------- | ----- | -------- | -------- | -------------- | --------- | --- | ------------------------------ | --- | -------------------------- | --- | --- | ------------- | --- |
| Chenglong            | Wang, | Jianfeng | Gao,     | Jiawei         | Han,      | and |                                |     |                            |     |     |               |     |
|                      |       |          |          |                |           |     | languagemodels.                |     | Preprint,arXiv:2506.10943. |     |     |               |     |
| ChengXiangZhai.2026. |       |          | Plugmem: | Atask-agnostic |           |     |                                |     |                            |     |     |               |     |
| plugin memory        |       | module   | for      | llm agents.    | Preprint, |     |                                |     |                            |     |     |               |     |
|                      |       |          |          |                |           |     | A ExperimentalDetails          |     |                            |     |     |               |     |
arXiv:2603.03296.
|     |     |     |     |     |     |     | A.1 DetailedDatasetStatistics |     |     |     |     |     |     |
| --- | --- | --- | --- | --- | --- | --- | ----------------------------- | --- | --- | --- | --- | --- | --- |
ChongruiYe,YuxiangLiu,YuWang,HaofeiYu,Yin-
| ing Zhao,  | Ge            | Liu, Julian | McAuley, |     | and     | Jiaxuan |         |                             |     |     |     |     |     |
| ---------- | ------------- | ----------- | -------- | --- | ------- | ------- | ------- | --------------------------- | --- | --- | --- | --- | --- |
|            |               |             |          |     |         |         | LoCoMo. | TheLoCoMobenchmarkprovidesa |     |     |     |     |     |
| You. 2026. | Auto-dreamer: |             | Learning |     | offline | mem-    |         |                             |     |     |     |     |     |
specializedevaluationforlong-contextreasoning
| ory consolidation |     | for | language | agents. | Preprint, |     |         |              |     |                |     |           |     |
| ----------------- | --- | --- | -------- | ------- | --------- | --- | ------- | ------------ | --- | -------------- | --- | --------- | --- |
|                   |     |     |          |         |           |     | through | 10 extensive |     | conversations, |     | featuring | an  |
arXiv:2605.20616.
|     |     |     |     |     |     |     | average | of 588 | turns | and | 16,618 | tokens | per di- |
| --- | --- | --- | --- | --- | --- | --- | ------- | ------ | ----- | --- | ------ | ------ | ------- |
ShichengYe,ChaoYu,KaiqiangKe,ChengdongXu, alogue. Our evaluation utilizes a total of 1,540
| and Yinqi                              | Wei. | 2025. | H2r: | Hierarchical |           | hind- |                                           |     |            |     |          |     |             |
| -------------------------------------- | ---- | ----- | ---- | ------------ | --------- | ----- | ----------------------------------------- | --- | ---------- | --- | -------- | --- | ----------- |
|                                        |      |       |      |              |           |       | human-annotated                           |     | questions, |     | covering |     | 841 single- |
| sightreflectionformulti-taskllmagents. |      |       |      |              | Preprint, |       |                                           |     |            |     |          |     |             |
| arXiv:2509.12810.                      |      |       |      |              |           |       | hop,282multi-hop,321temporalreasoning,and |     |            |     |          |     |             |
96
|               |     |          |      |       |       |      | open-domain |     | questions. |     | This | distribution | en- |
| ------------- | --- | -------- | ---- | ----- | ----- | ---- | ----------- | --- | ---------- | --- | ---- | ------------ | --- |
| Yunpeng Zhai, |     | Shuchang | Tao, | Cheng | Chen, | Anni |             |     |            |     |      |              |     |
suresabalancedassessmentofbothsimpleretrieval
| Zou, Ziqian | Chen, | Qingxu | Fu, | Shinji | Mai, | Li Yu, |     |     |     |     |     |     |     |
| ----------- | ----- | ------ | --- | ------ | ---- | ------ | --- | --- | --- | --- | --- | --- | --- |
andcomplexlogicalsynthesis.
| Jiaji Deng,                             | Zouying |       | Cao, Zhaoyang |               | Liu, | Bolin     |           |     |                                 |     |     |     |     |
| --------------------------------------- | ------- | ----- | ------------- | ------------- | ---- | --------- | --------- | --- | ------------------------------- | --- | --- | --- | --- |
| Ding, and                               | Jingren | Zhou. | 2025.         | Agentevolver: |      | To-       |           |     |                                 |     |     |     |     |
|                                         |         |       |               |               |      |           | Mind2Web. |     | Thisdatasetservesasalarge-scale |     |     |     |     |
| wardsefficientself-evolvingagentsystem. |         |       |               |               |      | Preprint, |           |     |                                 |     |     |     |     |
arXiv:2511.10395. testbedforgeneralistwebagents,featuring2,350
|     |     |     |     |     |     |     | open-ended | tasks | harvested |     | from | 137 | real-world |
| --- | --- | --- | --- | --- | --- | --- | ---------- | ----- | --------- | --- | ---- | --- | ---------- |
GuibinZhang,MuxinFu,GuanchengWan,MiaoYu,
|                                |     |     |     |     |           |     | websites   | across | 31 domains.  |     | The  | environmental |      |
| ------------------------------ | --- | --- | --- | --- | --------- | --- | ---------- | ------ | ------------ | --- | ---- | ------------- | ---- |
| KunWang,andShuichengYan.2025a. |     |     |     |     | G-memory: |     |            |        |              |     |      |               |      |
|                                |     |     |     |     |           |     | complexity | is     | significant, |     | with | an average    | page |
Tracinghierarchicalmemoryformulti-agentsystems.
Preprint,arXiv:2506.07398. size of 1,135 DOM elements and tasks requir-
inganaverageof7.3discreteactionstocomplete.
| Guibin Zhang, | Haotian | Ren, | Chong | Zhan, | Zhenhong |     |     |     |     |     |     |     |     |
| ------------- | ------- | ---- | ----- | ----- | -------- | --- | --- | --- | --- | --- | --- | --- | --- |
Wespecificallyevaluatethemodel’sgeneralization
| Zhou, JunhaoWang, |     | HeZhu, |     | WangchunshuZhou, |     |     |     |     |     |     |     |     |     |
| ----------------- | --- | ------ | --- | ---------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
and Shuicheng Yan. 2025b. Memevolve: Meta- acrossthreedimensions: cross-task,cross-website,
| evolution | of  | agent memory |     | systems. | Preprint, |     |     |     |     |     |     |     |     |
| --------- | --- | ------------ | --- | -------- | --------- | --- | --- | --- | --- | --- | --- | --- | --- |
andcross-domainscenarios.
arXiv:2512.18746.
|                |     |        |       |         |      |     | GAIA. | Evaluation |     | on the | GAIA | benchmark | is  |
| -------------- | --- | ------ | ----- | ------- | ---- | --- | ----- | ---------- | --- | ------ | ---- | --------- | --- |
| Haozhen Zhang, |     | Quanyu | Long, | Jianzhu | Bao, | Tao |       |            |     |        |      |           |     |
conductedacross165curatedtasksspanningthree
| Feng, Weizhi |     | Zhang,    | Haodong  | Yue, | and          | Wenya |                                          |     |     |     |     |     |        |
| ------------ | --- | --------- | -------- | ---- | ------------ | ----- | ---------------------------------------- | --- | --- | --- | --- | --- | ------ |
|              |     |           |          |      |              |       | levelsofincreasingoperationaldifficulty. |     |     |     |     |     | Theset |
| Wang. 2026a. |     | Memskill: | Learning |      | and evolving |       |                                          |     |     |     |     |     |        |
memory skills for self-evolving agents. Preprint, includes53Level-1tasksfocusedonbasictoolus-
arXiv:2602.02474.
ageandretrieval,86Level-2tasksrequiringmulti-
stepplanningandintermediatereasoning,and26
ShengtaoZhang,JiaqianWang,RuiwenZhou,Junwei
Liao,YuchenFeng,WeinanZhang,YingWen,Zhiyu Level-3tasksinvolvinglong-horizonexecutionand
Li, Feiyu Xiong, Yutao Qi, Bo Tang, and Muning multi-modalintegration.
| Wen.2026b. | Memrl: |     | Self-evolvingagentsviarun- |     |     |     |     |     |     |     |     |     |     |
| ---------- | ------ | --- | -------------------------- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
time reinforcement learning on episodic memory. A.2 ImplementationDetails
Preprint,arXiv:2601.03192.
|     |     |     |     |     |     |     | LoCoMo. | For | the | LoCoMo |     | benchmark, |     |
| --- | --- | --- | --- | --- | --- | --- | ------- | --- | --- | ------ | --- | ---------- | --- |
ZeyuZhang,QuanyuDai,XiaoheBo,ChenMa,RuiLi,
|     |     |     |     |     |     |     | all retrieval-based |     |     | methods |     | utilize | the |
| --- | --- | --- | --- | --- | --- | --- | ------------------- | --- | --- | ------- | --- | ------- | --- |
XuChen,JiemingZhu,ZhenhuaDong,andJi-Rong
|                                 |                               |     |     |     |             |     | text-embedding-3-small |                                    |     |     | model | for | generating |
| ------------------------------- | ----------------------------- | --- | --- | --- | ----------- | --- | ---------------------- | ---------------------------------- | --- | --- | ----- | --- | ---------- |
| Wen.2025c.                      | Asurveyonthememorymechanismof |     |     |     |             |     |                        |                                    |     |     |       |     |            |
|                                 |                               |     |     |     |             |     | embeddings.            | Thespecificretrievalconfigurations |     |     |       |     |            |
| largelanguagemodel-basedagents. |                               |     |     |     | ACMTransac- |     |                        |                                    |     |     |       |     |            |
tionsonInformationSystems,43(6):1–47. for each baseline are as follows: ⃝1 Zep and ⃝2

Mem0 utilize their respective commercial APIs atedmodelsthroughGoogle’sfunctionalprogram-
toretrievememorycontexts,extractingthetop-10 minginterface;⃝2 OpenAIDeepResearchlever-
relevantmemoriesforeachspeaker,whicharethen ageso1/o3seriesmodelswithintegratedchain-of-
integrated for response generation. ⃝3 A-MEM thoughtandreinforcementlearningoptimization;
performs a global search to retrieve the top-40 ⃝3 Magnetic-1employsano1-basedopen-source
overallentries. ⃝4 MemoryOSisimplementedasa agenticinfrastructure;⃝4 AgentKBincorporates
three-tierhierarchicalsystemfeaturingexhaustive an offline knowledge base pre-indexed with do-
recall of all Short-Term Memory (STM) pages, mainexpertise;⃝5 Alitausesmulti-modelorches-
a two-stage selection for Mid-Term Memory tration (Claude 3.7 Sonnet + GPT-4o) with dy-
(MTM) (comprising the top-5 segments and namicmodelselection;⃝6 Smolagentsimplements
top-10 dialogue pages), and the extraction of the a lightweight two-agent architecture (manager +
top-10 relevant entries from Long-term Personal toolagent). Ourevaluationsof⃝7 Flash-Searcher
Memory (LPM). ⃝5 Nemori retrieves the top-10 (baseline),⃝8 MemEvolve,and⃝9 FluxMemare
episodicmemoriesandtop-20semanticmemories conducted within the Flash-Searcher framework,
(m = 2k). ⃝6 LightMemextractsthetop-40total configured with 40 maximum steps, 8-step plan-
entries through its retrieval pipeline. ⃝7 MIRIX ning intervals. Flash-Searcher operates without
utilizes a multi-agent active retrieval mechanism, memoryaugmentation(32,768completiontokens
generatingautomatedtopicstoextractthetop-10 per call). MemEvolve employs meta-evolved ar-
entriesfromeachofitssixmemorybanks,totaling chitecturesthrough3iterations,60trajectoriesper
up to 60 entries. ⃝8 EverMemOS employs round with 40 new + 20 reused tasks, (K=1) sur-
a hierarchical architecture based on memory vivor,(S=3)descendants.
scenes(MemScene)andmemorycells(MemCell),
utilizinghybridretrieval(Dense+BM25)combined
with a reranking strategy to extract the top-10
thematicscenesandtop-10narrativesnippets.
Mind2Web. FortheMind2Webbenchmark,all
baseline methods are evaluated under an offline
protocolandfollowtheirrespectivenativeevalua-
tionpipelines,usingGPT-4.1-miniandGemini-2.5-
flash as the base models.: ⃝1 AWM is evaluated
undertwosettings. Intheoriginalsetting,weap-
ply top-k = 5 candidate filtering on the current
page. However, due to the large number of page
elements,restrictingthecurrentpagetotop-kcan-
didatesdiscardssubstantialinformationandeffec-
tivelyreducestheactionselectiondifficulty,which
deviatesfromrealisticwebinteraction. Therefore,
in the realistic setting, we disable top-k filtering
forthecurrentpageandinsteadprovidethemodel
with all candidate elements, including both posi-
tiveandnegativeelements,tobettersimulatereal-
world conditions. In both settings, we keep the
same configuration for visited-history elements,
using top-k = 3 retrieval from previously visited
pages. ⃝2 ReasoningBankTheagentpredictsac-
tions with retrieved reasoning memories injected
into the prompt, and scores are computed by the
standardevaluationscriptoverthetestset.
GAIA. For the GAIA benchmark, all methods
areevaluatedwithasinglerunpertask: ⃝1 Lang-
fun operates with Claude 3.7 Sonnet and associ-