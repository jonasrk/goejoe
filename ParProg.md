#1

* Technologien/Entwicklungen für mehr Performance? -> Frequenz erhöhen, Caches vergrößern, mehr ILP, Parallelisierung
* Was gibt es für ILP-Mechanismen?
* Warum parallelisieren? (Speedup, Scaleup)
* Amdahls Law, Gustafsons Law
* Coffman Conditions aufzählen + an selbst gewähltem Beispiel zeigen, wie man eine davon verletzen kann
* Surface-to-Volume-Effekt mit Fosters Methodology in Verbindung bringen
* Was ist das besondere an GPUs? Ein GPU-Programmiermodell nennen. (OpenCL)
* Memory Latency Hiding in GPUs erklären
* Prinzip von Ghost Cells erklären

#2

* welche Hardware-Entwicklungen nötigen uns, über Parallelisierung nachzudenken (Moore's Law, 3 Walls)
* wichtig zu erwähnen, dass Memory Wall durch Parallelisierung nur schlimmer wird
* Foster-Methode anhand von Heatmap erklären
* was mir bei Schritt 1 nicht klar war: in Bereiche einheitlichen Rechenaufwands einteilen -> wollten sie explizit hören, haben mich aber drauf hingewiesen: was wäre denn, wenn sie in jedem Feld die Fakultät berechnen müssten (1!, 2!, 3!, ...)
* was sind und wie funktionieren Monitore
* Tröger wollte dann noch wissen, welche Variante in Java implementiert ist (notify() oder notifyAll() sucht sich Entwickler aus, Monitorkontrolle behält der Thread, der notify...() aufruft)
* Reduce erklären, und sagen welche Frameworks aus den Übungen es unterstützen (OpenMP, OpenMPI)
* Unterschied Tasks und Threads
* Work-Stealing bei Tasks: was ist das, was hat es für Vorteile, wollte auch hören dass neue Tasks oben auf den Stack gelegt, und geklaut von unten wird (oben auflegen um Locality zu wahren)
* Prinzip GPU Hardware: Streaming Multiprocessors, die Thread-Gruppen (Warps) synchron ausführen
* Parallelität ohne Multithreading? (ILP)
* Arten von Multithreading auf einem Kern: simultaneous, interleaved
* Flynn's taxonomy erläutern, wo ordnen sich GPUs ein
* SM-Programmiermodelle (Actors, Message Passing aus SN gehen auch in SM, dann sind wir abgeschweift zu etwas anderem)
* Abschlußfrage: was ist Ihre Lieblingsprogrammiersprache :D

#3

* Teile von dem was vorher schon genannt wurde (Surface-To-Volume, Amhdahl vs. Gustafson, ...)
* Viel zu Franks Teil, teliweise sehr detailliert, hier nur Beispielhaft: 
* Wie sehen denn die ILP Mechanismen in einem Kern einer Xeon Phi aus? (Superscalar, ähnlich VLIW)
* LoG P: Was versteht man genau unter dem Overhead? (Marshalling der Nachrichten, etc.)
*  Auf einer XeonPhi werden 4 Workgroups gleichzeitig pro Prozessor ausgeführt, ist es Pflicht, dass diese Workgroups das selbe tun? (Nö, kann aber sinnvoll sein.)

#4

* Warum parallelisieren? -> Scaleup, Speedup
* ILP detailliert
* Surface-To-Volume
* Amdahl/Gustafson mit Formel und Diagramm für Amdahl (zumindest die Formel soll man auch unaufgefordert aufschreiben)
* passend dazu LogP für die Größe des sequentiellen Anteils
* Monitors detailliert
* Warum gehören MPI und GPUs zu SPMD
* Was ist das Äquivalent von Rank und Communicator aus MPI in GPUs? - ID und Workgroup
* OpenCL nur kurz, ein bisschen über Kernel, NDRange, die vergebenen IDs
* Was machen CPUs und GPUs zum Memory Latency Hiding? - CPU: Caching, SMT (hierzu ein paar Details), Instruction Reordering; GPU: Selbst wenn nur einziger Core warten muss, wird die ganze zugehörige Warp gegen eine lauffähige Warp ausgetauscht
* Oberflächlich zu zukünftigen Hardwareentwicklungen, nur ein paar Anwendungsgebiete nennen und erwähnen, dass wir wohl hybride Systeme haben werden
* kurz was zu den Berkeley Dwarfs
* Vergleich von CSP und Actors
* Deadlocks in Actors möglich? - Mit passender Begründung sind wohl beide Antworten möglich.

#5

* Am Anfang ging es um parallel vs. nebenläufig, Speed up vs. Scale up und Amdahl und Gustafson.
* Ausgehend von den Formeln für Amdahl und Gustafson ging es dann darum, was das mit Surface to Volume zu tun hat.
* Dann kam die Frage ob es auch Scale up wäre, wenn man einen zweiten Würfel danebenmalt. Eigentlich wollte er wohl darauf hinauf, dass das ein zweites völlig unabhäniges Programm wäre, das ggf. parallel zu dem ersten läuft. Ich habe die Annahme getroffen, dass sie auch miteinander kommunizieren, also ein Programm sind, und das war anscheinend auch in Ordnung.
* Von nun an gab es ein ziemlich zusammenhangloses Springen zwischen verschiedensten Themen:
* PRAM, BSP und LogP beschreiben, warum braucht man sowas überhaupt und jeweils ein Beispiel nennen
* sowohl OpenCL als auch MPI sind Beispiele für SPMD - Warum?
* was ist bei OpenCL das, was bei MPI die Ranks sind (hierbei habe ich nur von globalen IDs für die Work items gesprochen, dann wollte Frank wissen, ob es auch eine ID innerhalb einer Workgroup gibt - die Antwort kenne ich allerdings immer noch nicht ^^)
* wichtig war ihnen, dass die "Aktivitäten" bei MPI "Prozesse" heißen; da ich das nicht von allein wusste, wollten sie dann, dass ich herleite, warum sie so heißen könnten
* da ich bei MPI fälschlicherweise den Begriff "Task" verwendet hatte, war nun auch OpenMP im Gespräch: Warum wird bei MPI beim Programmaufruf mit angegeben, wieviele Prozesse man haben will, während OpenMP das selbst macht (hier hat Tröger selbst gesagt, dass das nicht in der Vorlesung dran war, von daher wird es wohl eine Bonusfrage gewesen sein und demnach reichte auch ein hinstammeln von Ideen und unfertigen Ansätzen)
* was sind hybride Systeme und was für Sprachen verwendet man da? (OpenMP für Shared Memory Teil und MPI für den Shared Nothing Teil)
* Dann wollte Tröger die Prüfung beenden, aber Frank hat nochmal eine kurze Frage zu Interconnections eingeworfen ("Welches ist das beste?"). Ich sollte dann am Ende noch die Verbindungsvarianten mit den meisten bzw. wenigsten Verbindungen kurz aufmalen. Außerdem wollten sie ein Beispiel, wo man jeden mit jedem verbindet.

#6

* Surface-To-Volume Erklärung und dann: Was passiert wenn sie den Würfel in zwei Hälften geteilt haben und dann das Volumen vergrößern? (Bisschen gestrauchelt. Lösung: Das Volumen wächst natürlich mehr, wegen dritter Potenz)
* Surface-To-Volume und Supercomputer: Was passiert denn, wenn man einen zweiten Würfel daneben stellt, sprich ein unabhängiges zweites Problem berechnet? (Hängt davon ab ob die Dinger unabhängig sind, oder abhängig. Wenn unabhängig, dann passiert ja nicht schlimmes)
* Wenn wir jetzt unabhängige Probleme haben, wie passt das zu Gustafson's Law? (Hängt von der Betrachtungsweise ab. Die seriellen Teile der Drei können ja jetzt auch parallel ausgeführt werden. Allerdings kommt ein serieller Teil hinzu, der die drei Programme startet)
* Ein Beispiel für OpenMP parallel for aufschreiben. Frank wollte das für jedes Element die Fakultät berechnet wird. Dann wollte er wissen, was das Problem mit den Schleifendurchläufen ist und wie man das löst. (Steigender Berechnungsaufwand, Loopverteilungsmodi in OpenMP)
* Work Stealing bei Task Parallelismus. Woher holt man die Tasks wo packt man sie in die Queue (Hatte ich nicht ganz drauf, aber mit Caching + Lokalität + Locking der Queues, die richtigen Probleme genannt)
* Diskussion von NUMA und Prinzip von PGAS Sprachen
* Welches ist das beste theoretische Hardwaremodell um Message Passing-Systeme zu beschreiben. (Habe zwischen BSP und LogP abgewogen)
* Wie würden sie vorgehen um LogP auf den Surface-Volume Effekt abzubilden?
* Inwiefern unterscheidet sich das Receive in MPI vom Receive im Actor Modell?
* Hilft einem das asynchrone Senden und Empfangen im Actor-Modell irgendwie bei den Coffman Conditions (Nein, aber macht es schwieriger sie alle zu erfüllen)
* Wie wird ein actorbasiertes Programm gestartet? (z.B. ein Actor, der dann andere erstellt)