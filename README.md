Анализируй. Сразу говорю класса Main не существует он разделён на Server, Player и Debug но в документации этого НЕТ

\# 📚 GOREBOX API DOCUMENTATION

\> Version: 2.1 BETA | Generated: 01.03.2026

\## 📑 Table of Contents

\- \[Hooks\](#hooks)

\- \[AudioClip\](#audioclip)

\- \[Bounds\](#bounds)

\- \[Component\](#component)

\- \[DamageSystem\](#damagesystem)

\- \[Environment\](#environment)

\- \[Event\](#event)

\- \[File\](#file)

\- \[GameObject\](#gameobject)

\- \[GoreDollMaster\](#goredollmaster)

\- \[GUI\](#gui)

\- \[Importer\](#importer)

\- \[Input\](#input)

\- \[InputTouchInfo\](#inputtouchinfo)

\- \[JSON\](#json)

\- \[LayerMask\](#layermask)

\- \[Main\](#main)

\- \[Material\](#material)

\- \[Matrix4x4\](#matrix4x4)

\- \[Mesh\](#mesh)

\- \[PenetrationInfo\](#penetrationinfo)

\- \[Physic\](#physic)

\- \[Player\](#player)

\- \[PlayerMaster\](#playermaster)

\- \[RaycastInfo\](#raycastinfo)

\- \[Sprite\](#sprite)

\- \[String\](#string)

\- \[Texture\](#texture)

\- \[Time\](#time)

\- \[Transform\](#transform)

\- \[Vector2\](#vector2)

\- \[Vector3\](#vector3)

\- \[Vector4\](#vector4)

\---

\## 📦 Hooks

\### p Awake

\`\`\`lua

function Awake()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается при загрузке экземпляра скрипта, до Start. Используйте для инициализации.

\*\*Example:\*\*

\`\`\`lua

function Awake()

-- Вызывается один раз при инициализации мода Main.SendChatMessageLocal("Мод инициализирован")
end

\`\`\`

\---

\### p Start

\`\`\`lua

function Start()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается один раз при инициализации скрипта мода.

\*\*Example:\*\*

\`\`\`lua

function Start()

-- Вызывается один раз при инициализации мода Main.SendChatMessageLocal("Мод инициализирован")
end

\`\`\`

\---

\### p Update

\`\`\`lua

function Update()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается каждый кадр. Используйте для основной логики, ввода и таймеров.

\*\*Example:\*\*

\`\`\`lua

function Update()

-- Пример: Проверка нажатия клавиши 'M' if Input.GetKeyDown("M") then Main.Log("Нажата клавиша M") end -- Пример: Клик мышью (0 = Левая, 1 = Правая, 2 = Колесико) if Input.GetMouseDown(0) then Main.Log("Нажата левая кнопка мыши") end
end

\`\`\`

\---

\### p LateUpdate

\`\`\`lua

function LateUpdate()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается каждый кадр после Update. Используется для камеры, чтобы избежать тряски.

\*\*Example:\*\*

\`\`\`lua

function LateUpdate()

-- Вызывается после Update. Используется редко.
end

\`\`\`

\---

\### p FixedUpdate

\`\`\`lua

function FixedUpdate()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается через фиксированные интервалы времени. Используйте для расчетов физики.

\*\*Example:\*\*

\`\`\`lua

function Start()

-- Инициализация переменной таймера Timer = 5.0
end

function FixedUpdate()

-- Таймер обратного отсчета (работает на физическом шаге) -- Проверка безопасности: убеждаемся, что таймер существует if Timer == nil then Timer = 5.0 end if Timer > 0 then Timer = Timer - 0.02 if Timer <= 0 then -- Отправляем сообщение, когда время вышло Main.SendChatMessageLocal("Таймер истек!") Timer = 5.0 -- Сброс таймера end end
end

\`\`\`

\---

\### p OnDestroy

\`\`\`lua

function OnDestroy()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается при уничтожении или удалении скрипта/объекта.

\*\*Example:\*\*

\`\`\`lua

function OnDestroy()

-- Вызывается при остановке или выгрузке скрипта Main.SendChatMessageLocal("Мод остановлен")
end

\`\`\`

\---

\### p OnGUI

\`\`\`lua

function OnGUI()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается несколько раз за кадр для отрисовки интерфейса и обработки событий UI.

\*\*Example:\*\*

\`\`\`lua

function OnGUI()

-- Проверка доступности GUI для предотвращения ошибок if GUI and Rect then if GUI.Button(Rect.New(50, 50, 200, 50), "Нажми меня") then Main.Log("Кнопка была нажата!") Main.SendChatMessageLocal("Вы нажали кнопку.") end end
end

\`\`\`

\---

\### p OnGUIOver

\`\`\`lua

function OnGUIOver()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается несколько раз за кадр для отрисовки интерфейса и обработки событий UI. Не обрывается при открытой консоли

\*\*Example:\*\*

\`\`\`lua

function OnGUIOver()

-- Проверка доступности GUI для предотвращения ошибок if GUI then if GUI.Button(Vector4.New(50, 50, 200, 50), "Нажми меня") then Main.Log("Кнопка была нажата!") Main.SendChatMessageLocal("Вы нажали кнопку.") end end
end

\`\`\`

\---

\### p OnActiveSceneChanged

\`\`\`lua

function OnActiveSceneChanged(oldScene, newScene)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается при смене карты/сцены.

\*\*Example:\*\*

\`\`\`lua

function OnActiveSceneChanged(oldScene,newScene)

Main.Log("Old Scene:" .. oldScene .. "New Scene:" .. newScene)
end

\`\`\`

\---

\### p OnGetRPC

\`\`\`lua

function OnGetRPC(data(string))

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается при получении RPC (сетевых данных).

\*\*Example:\*\*

\`\`\`lua

function OnGetRPC(data)

Main.SendChatMessageLocal("Data: " .. data)
end

\`\`\`

\---

\### p OnPlayerJoined

\`\`\`lua

function OnPlayerJoined(player)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда другой игрок подключается к серверу.

\*\*Example:\*\*

\`\`\`lua

function OnPlayerJoined(player)

Main.SendChatMessage("Добро пожаловать, " .. player.GetName() .. "!")
end

\`\`\`

\---

\### p OnPlayerLeft

\`\`\`lua

function OnPlayerLeft(player)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда другой игрок отключается от сервера.

\*\*Example:\*\*

\`\`\`lua

function OnPlayerLeft(player)

Main.SendChatMessage("До свидания" .. player.GetName() .. "!")
end

\`\`\`

\---

\### p OnPlayerSpawned

\`\`\`lua

function OnPlayerSpawned(player)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда другой игрок возрождается

\*\*Example:\*\*

\`\`\`lua

function OnPlayerSpawned(player)

Main.SendChatMessage("Ура. " .. player.GetName() .. " Возродился!")
end

\`\`\`

\---

\### p OnKilledPlayer

\`\`\`lua

function OnKilledPlayer(player, killer)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда локальный игрок кого-то убивает.

\*\*Example:\*\*

\`\`\`lua

function OnKilledPlayer(player, killer)

Main.SendChatMessageLocal(player.GetName() .. " был убит игроком " .. killer.GetName())
end

\`\`\`

\---

\### p OnChatMessage

\`\`\`lua

function OnChatMessage(message, sender)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается при получении сообщения в чате.

\*\*Example:\*\*

\`\`\`lua

function OnChatMessage(message, sender)

-- Логирование сообщения в консоль для отладки Main.Log("Чат: " .. message) -- Простая проверка команд if message == "!ping" then Main.SendChatMessage("Pong!") end
end

\`\`\`

\---

\### p OnLocalDied

\`\`\`lua

function OnLocalDied()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда локальный игрок умирает.

\*\*Example:\*\*

\`\`\`lua

function OnLocalDied()

Main.SendChatMessage("Я умер!")
end

\`\`\`

\---

\### p OnKilledSelf

\`\`\`lua

function OnKilledSelf()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда локальный игрок совершает суицид.

\*\*Example:\*\*

\`\`\`lua

function OnKilledSelf()

Main.SendChatMessage("Я покончил с собой.")
end

\`\`\`

\---

\### p OnLocalInfected

\`\`\`lua

function OnLocalInfected()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда локальный игрок заражается.

\*\*Example:\*\*

\`\`\`lua

function OnLocalInfected()

Main.SendChatMessageLocal("Вы заражены!")
end

\`\`\`

\---

\### p OnLocalHealed

\`\`\`lua

function OnLocalHealed()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда локальный игрок лечится.

\*\*Example:\*\*

\`\`\`lua

function OnLocalHealed()

Main.SendChatMessageLocal("Здоровье восстановлено.")
end

\`\`\`

\---

\### p OnLocalWakeUp

\`\`\`lua

function OnLocalWakeUp()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда локальный игрок приходит в сознание.

\*\*Example:\*\*

\`\`\`lua

function OnLocalWakeUp()

Main.SendChatMessageLocal("Очнулся.")
end

\`\`\`

\---

\### p OnLocalKnockout

\`\`\`lua

function OnLocalKnockout()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда локальный игрок отправляется в нокаут.

\*\*Example:\*\*

\`\`\`lua

function OnLocalKnockout()

Main.SendChatMessage("Меня вырубили!")
end

\`\`\`

\---

\### p OnLocalSpawned

\`\`\`lua

function OnLocalSpawned()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается при спавне персонажа локального игрока в мир.

\*\*Example:\*\*

\`\`\`lua

function OnLocalSpawned()

Main.SendChatMessageLocal("Возродился.")
end

\`\`\`

\---

\### p OnLocalRagdoll

\`\`\`lua

function OnLocalRagdoll()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда локальный игрок переходит в режим рэгдолла.

\*\*Example:\*\*

\`\`\`lua

function OnLocalRagdoll()

Main.SendChatMessageLocal("Режим тряпичной куклы (Ragdoll) активен.")
end

\`\`\`

\---

\### p OnLocalGetUp

\`\`\`lua

function OnLocalGetUp()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда локальный игрок встает из режима рэгдолла.

\*\*Example:\*\*

\`\`\`lua

function OnLocalGetUp()

Main.SendChatMessageLocal("Встаю...")
end

\`\`\`

\---

\### p OnLocalEmote

\`\`\`lua

function OnLocalEmote(emoteName)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда локальный игрок начинает эмоцию.

\*\*Example:\*\*

\`\`\`lua

function OnLocalEmote(emoteName)

Main.SendChatMessageLocal("Эмоция: " .. emoteName)
end

\`\`\`

\---

\### p OnLocalEndEmote

\`\`\`lua

function OnLocalEndEmote()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается, когда локальный игрок заканчивает эмоцию.

\*\*Example:\*\*

\`\`\`lua

function OnLocalEndEmote()

Main.SendChatMessageLocal("Эмоция завершена.")
end

\`\`\`

\---

\### p OnTakeDamage

\`\`\`lua

function OnTakeDamage(damage, limb, player)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается при получении урона. Возвращает кол-во, часть тела и атакующего.

\*\*Example:\*\*

\`\`\`lua

function OnTakeDamage(damage, limb, attacker)

Main.SendChatMessageLocal("Урон: " .. damage .. " по части тела: " .. limb)
end

\`\`\`

\---

\### p OnWeaponHit

\`\`\`lua

function OnWeaponHit(hitPos, target)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается когда игрок попал выстрелом из классического оружия по цели

\*\*Example:\*\*

\`\`\`lua

function OnWeaponHit(hitPos, target)

if target \\\~= nil then Main.Log("Попадание в точке: " .. hitPos.ToString() .. " в обьект с именем: " .. target.Name) end
end

\`\`\`

\---

\### p OnWeaponFire

\`\`\`lua

function OnWeaponFire()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается когда классическое оружие произвело выстрел

\*\*Example:\*\*

\`\`\`lua

function OnWeaponFire()

Main.Log("Выстрел!")
end

\`\`\`

\---

\### p OnRC2Spawn

\`\`\`lua

function OnRC2Spawn(objTransform)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывается когда игрок(локальный) создает проп с помощью Reality Crusher 2

\*\*Example:\*\*

\`\`\`lua

function OnRC2Spawn(objTransform)

Main.SendChatMessageLocal("Заспавнил проп с именем: " .. objTransform.GameObject.Name)
end

\`\`\`

\---

\### p OnUnload

\`\`\`lua

function OnUnload()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* ОЧЕНЬ ВАЖНЫЙ ЕВЕНТ! Вызывается при выгрузке мода. Зачастую используется для оптимизации мода. К примеру, удаления заспавненых обьектов

\*\*Example:\*\*

\`\`\`lua

function OnUnload()

GameObject.ClearObjects()
end

function Update()

GameObject.Create("empty")
end

\`\`\`

\---

\## 📦 AudioClip

\### p Length

\`\`\`lua

AudioClip.Length

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Длительность аудиоклипа в секундах.

\---

\### p Samples

\`\`\`lua

AudioClip.Samples

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Общее количество сэмплов в клипе.

\---

\### p Channels

\`\`\`lua

AudioClip.Channels

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Количество аудиоканалов (1 = Моно, 2 = Стерео).

\---

\### p Frequency

\`\`\`lua

AudioClip.Frequency

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Частота дискретизации клипа в Герцах.

\---

\## 📦 Bounds

\### ƒ New

\`\`\`lua

Bounds.New(center, size)

\`\`\`

\*\*Return:\*\* \`Bounds\`

\*\*Description:\*\* Создает ограничивающую коробку (AABB) из центра и размера.

\---

\### p bounds

\`\`\`lua

Bounds.bounds

\`\`\`

\*\*Return:\*\* \`Bounds\`

\*\*Description:\*\* Внутренняя ссылка на нативную структуру Unity Bounds.

\---

\### p center

\`\`\`lua

Bounds.center

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Центр коробки.

\---

\### p size

\`\`\`lua

Bounds.size

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Общий размер коробки (Ширина, Высота, Глубина).

\---

\### p min

\`\`\`lua

Bounds.min

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Нижний-левый-задний угол коробки.

\---

\### p max

\`\`\`lua

Bounds.max

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Верхний-правый-передний угол коробки.

\---

\### p extents

\`\`\`lua

Bounds.extents

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Расстояние от центра до края (половина размера).

\---

\### ƒ ToBounds

\`\`\`lua

Bounds.ToBounds()

\`\`\`

\*\*Return:\*\* \`Bounds\`

\*\*Description:\*\* Клонирует объект Bounds.

\---

\## 📦 Component

\### p Active

\`\`\`lua

Component.Active

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Включает или отключает компонент на игровом объекте.

\---

\### p GameObject

\`\`\`lua

Component.GameObject

\`\`\`

\*\*Return:\*\* \`GameObject\`

\*\*Description:\*\* Возвращает GameObject, к которому прикреплен этот компонент.

\---

\### p Name

\`\`\`lua

Component.Name

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Точное имя типа компонента (например, 'BoxCollider', 'Light').

\---

\### ƒ GetComponents

\`\`\`lua

Component.GetComponents()

\`\`\`

\*\*Return:\*\* \`string\[\]\`

\*\*Description:\*\* Возвращает список всех остальных компонентов, прикрепленных к тому же объекту.

\---

\### ƒ GetField

\`\`\`lua

Component.GetField(name)

\`\`\`

\*\*Return:\*\* \`object\`

\*\*Description:\*\* Использует рефлексию для чтения публичного поля по имени. Нужно для доступа к свойствам, которых нет в API.

\---

\### ƒ SetField

\`\`\`lua

Component.SetField(name, value)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Использует рефлексию для установки значения публичного поля по имени.

\---

\### ƒ GetFields

\`\`\`lua

Component.GetFields()

\`\`\`

\*\*Return:\*\* \`string\[\]\`

\*\*Description:\*\* Возвращает список имен всех доступных публичных полей этого компонента.

\---

\### ƒ CallMethod

\`\`\`lua

Component.CallMethod(methodName, args)

\`\`\`

\*\*Return:\*\* \`object\`

\*\*Description:\*\* Выполняет публичный метод компонента по имени через рефлексию, передавая аргументы.

\---

\### ƒ GetMethods

\`\`\`lua

Component.GetMethods()

\`\`\`

\*\*Return:\*\* \`string\[\]\`

\*\*Description:\*\* Возвращает список имен всех доступных публичных методов этого компонента.

\---

\### ƒ GetMethodForm

\`\`\`lua

Component.GetMethodForm(methodName)

\`\`\`

\*\*Return:\*\* \`string\[\]\`

\*\*Description:\*\* Возвращает информацию о типах аргументов, необходимых для конкретного метода.

\---

\## 📦 DamageSystem

\### p Health

\`\`\`lua

DamageSystem.Health

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Текущее здоровье этой конкретной части тела или объекта.

\---

\### p MaxHealth

\`\`\`lua

DamageSystem.MaxHealth

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Максимально возможное здоровье для этой части.

\---

\### p CollisionMagnitude

\`\`\`lua

DamageSystem.CollisionMagnitude

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Порог силы удара, необходимый для нанесения физического урона.

\---

\### p Name

\`\`\`lua

DamageSystem.Name

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Название части тела (напр., 'Head', 'LeftArm').

\---

\### p damageSystemType

\`\`\`lua

DamageSystem.damageSystemType

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Целое число, представляющее тип материала (Плоть, Дерево, Металл и т.д.).

\---

\### ƒ TakeDamage

\`\`\`lua

DamageSystem.TakeDamage(damage, bldMultiper, dismember)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Наносит урон объекту с учетом множителя кровотечения и возможности расчленения.

\---

\## 📦 Environment

\### p Time

\`\`\`lua

Environment.Time

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Текущее время суток в игровом мире.

\---

\### p DayNightCycle

\`\`\`lua

Environment.DayNightCycle

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Включает или отключает автоматическую смену дня и ночи.

\---

\### p Rain

\`\`\`lua

Environment.Rain

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Включает или отключает эффект дождя.

\---

\### p Thunder

\`\`\`lua

Environment.Thunder

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Включает или отключает гром и молнии.

\---

\### p Snow

\`\`\`lua

Environment.Snow

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Включает или отключает эффект снега.

\---

\## 📦 Event

\### ƒ New

\`\`\`lua

Event.New(unityEvent)

\`\`\`

\*\*Return:\*\* \`Event\`

\*\*Description:\*\* Создает новый объект события. Используйте для создания собственных сигналов между скриптами.

\---

\### p targetEvent

\`\`\`lua

Event.targetEvent

\`\`\`

\*\*Return:\*\* \`UnityEvent\`

\*\*Description:\*\* Внутренняя ссылка на сырое событие Unity. Редко используется напрямую в Lua.

\---

\### ƒ AddListener

\`\`\`lua

Event.AddListener(luaFunction)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Подписывает Lua-функцию на событие. Функция будет вызвана при каждом срабатывании события.

\---

\### ƒ Invoke

\`\`\`lua

Event.Invoke(args)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывает событие, запуская все функции, которые на него подписаны.

\---

\### ƒ ToString

\`\`\`lua

Event.ToString()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает строковое представление объекта события для отладки.

\---

\## 📦 File

\### ƒ GetModName

\`\`\`lua

File.GetModName()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает имя папки, в которой находится текущий мод.

\---

\### ƒ GetModDescription

\`\`\`lua

File.GetModDescription()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает текст описания, указанный в метаданных мода.

\---

\### ƒ GetModVersion

\`\`\`lua

File.GetModVersion()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает строку с версией текущего мода.

\---

\### ƒ GetModSize

\`\`\`lua

File.GetModSize()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает общий размер папки мода в читаемом формате.

\---

\### ƒ GetModRoot

\`\`\`lua

File.GetModRoot()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает полный системный путь к папке текущего мода.

\---

\### ƒ GetModsRoot

\`\`\`lua

File.GetModsRoot()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает полный системный путь к глобальной папке 'Mods' игры.

\---

\### ƒ FolderExist

\`\`\`lua

File.FolderExist(path)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет, существует ли папка по указанному пути.

\---

\### ƒ FileExist

\`\`\`lua

File.FileExist(path)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет, существует ли файл по указанному пути.

\---

\### ƒ CreateFolder

\`\`\`lua

File.CreateFolder(path)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Создает новую папку по указанному пути, если она еще не существует.

\---

\### ƒ ExportFile

\`\`\`lua

File.ExportFile(path, content)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Записывает текст в файл по указанному пути. Перезаписывает файл, если он существует.

\---

\### ƒ ImportFile

\`\`\`lua

File.ImportFile(path)

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Читает всё содержимое текстового файла и возвращает его как строку.

\---

\### p GetPlayerPrefsVal

\`\`\`lua

File.GetPlayerPrefsVal

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Получает числовое значение из локальных настроек клиента (Unity PlayerPrefs).

\---

\### p SetPlayerPrefsVal

\`\`\`lua

File.SetPlayerPrefsVal

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Сохраняет числовое значение в локальные настройки клиента (сохраняется между запусками игры).

\---

\### p GetPlayerPrefsStr

\`\`\`lua

File.GetPlayerPrefsStr

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Получает строковое значение из локальных настроек клиента.

\---

\### p SetPlayerPrefsStr

\`\`\`lua

File.SetPlayerPrefsStr

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Сохраняет строковое значение в локальные настройки клиента.

\---

\### ƒ DoString

\`\`\`lua

File.DoString(code)

\`\`\`

\*\*Return:\*\* \`DynValue\`

\*\*Description:\*\* выполняет код, заданный в аргументе

\---

\### ƒ DoFile

\`\`\`lua

File.DoFile(path)

\`\`\`

\*\*Return:\*\* \`DynValue\`

\*\*Description:\*\* Выполняет код по заданному пути. В основном используется для подключения библиотек

\---

\### ƒ GetAllFolders

\`\`\`lua

File.GetAllFolders(path)

\`\`\`

\*\*Return:\*\* \`string\[\]\`

\*\*Description:\*\* Возвращает список всех доступных папок по пути

\---

\### ƒ GetAllFiles

\`\`\`lua

File.GetAllFiles(path)

\`\`\`

\*\*Return:\*\* \`string\[\]\`

\*\*Description:\*\* Возвращает список всех доступных файлов по пути

\---

\## 📦 GameObject

\### ƒ New

\`\`\`lua

GameObject.New(gameObject, host)

\`\`\`

\*\*Return:\*\* \`GameObject\`

\*\*Description:\*\* Оборачивает сырой объект Unity в совместимый с Lua GameObject. Редко используется напрямую.

\---

\### ƒ Create

\`\`\`lua

GameObject.Create(name)

\`\`\`

\*\*Return:\*\* \`GameObject\`

\*\*Description:\*\* Создает новый пустой, невидимый GameObject. Часто используется как папка или контейнер для скриптов.

\---

\### ƒ FindByName

\`\`\`lua

GameObject.FindByName(name)

\`\`\`

\*\*Return:\*\* \`GameObject\`

\*\*Description:\*\* Ищет во всей сцене объект с указанным именем. ВНИМАНИЕ: Очень медленно! Не вызывайте в Update.

\---

\### ƒ FindAllByTag

\`\`\`lua

GameObject.FindAllByTag(tagName)

\`\`\`

\*\*Return:\*\* \`GameObject\[\]\`

\*\*Description:\*\* Возвращает список всех объектов с определенным Тегом (напр., 'Enemy', 'Player').

\---

\### ƒ FindAllByComponent

\`\`\`lua

GameObject.FindAllByComponent(cName)

\`\`\`

\*\*Return:\*\* \`GameObject\[\]\`

\*\*Description:\*\* Возвращает список всех объектов с определенным Компонентом (напр., 'Light').

\---

\### ƒ Instantiate

\`\`\`lua

GameObject.Instantiate(path)

\`\`\`

\*\*Return:\*\* \`GameObject\`

\*\*Description:\*\* Спавнит копию префаба (ассета). Нужно использовать точный путь из списка ассетов.

\---

\### ƒ InstantiatePermanent

\`\`\`lua

GameObject.InstantiatePermanent(path)

\`\`\`

\*\*Return:\*\* \`GameObject\`

\*\*Description:\*\* Спавнит объект, который остается при смене сцены или перезагрузке. Используйте осторожно.

\---

\### ƒ Copy

\`\`\`lua

GameObject.Copy(original)

\`\`\`

\*\*Return:\*\* \`GameObject\`

\*\*Description:\*\* Создает точный дубликат существующего объекта в сцене.

\---

\### ƒ ClearObjects

\`\`\`lua

GameObject.ClearObjects()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Удаляет все объекты, созданные этим скриптом. Полезно для команд очистки.

\---

\### ƒ Destroy

\`\`\`lua

GameObject.Destroy()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Удаляет объект из игры. Можно указать задержку в секундах.

\---

\### p Name

\`\`\`lua

GameObject.Name

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Имя объекта в иерархии.

\---

\### p Active

\`\`\`lua

GameObject.Active

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Показывает/скрывает объект. False отключает скрипты и рендеринг.

\---

\### p Layer

\`\`\`lua

GameObject.Layer

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* ID физического слоя (0-31). Определяет логику столкновений.

\---

\### p Tag

\`\`\`lua

GameObject.Tag

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Тег, идентифицирующий тип объекта (напр., 'Untagged', 'Player').

\---

\### p Material

\`\`\`lua

GameObject.Material

\`\`\`

\*\*Return:\*\* \`Material\`

\*\*Description:\*\* Основной материал объекта. Изменение этого меняет внешний вид.

\---

\### p Transform

\`\`\`lua

GameObject.Transform

\`\`\`

\*\*Return:\*\* \`Transform\`

\*\*Description:\*\* Доступ к компоненту Transform (Позиция, Вращение, Размер).

\---

\### ƒ Owner

\`\`\`lua

GameObject.Owner()

\`\`\`

\*\*Return:\*\* \`Player\`

\*\*Description:\*\* Игрок, владеющий объектом в сети. Только владелец может двигать его физикой.

\---

\### ƒ TransferOwnership

\`\`\`lua

GameObject.TransferOwnership(newOwner)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Передает сетевые права другому игроку. Требуется для физики в мультиплеере.

\---

\### ƒ IsValid

\`\`\`lua

GameObject.IsValid()

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет, существует ли объект. Всегда проверяйте перед использованием.

\---

\### ƒ AddComponent

\`\`\`lua

GameObject.AddComponent(name)

\`\`\`

\*\*Return:\*\* \`Component\`

\*\*Description:\*\* Добавляет компонент Unity по имени (напр., 'Rigidbody', 'Light').

\---

\### ƒ RemoveComponent

\`\`\`lua

GameObject.RemoveComponent(name)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Удаляет конкретный компонент с объекта.

\---

\### ƒ GetComponent

\`\`\`lua

GameObject.GetComponent(name)

\`\`\`

\*\*Return:\*\* \`Component\`

\*\*Description:\*\* Находит компонент на объекте для чтения/записи полей.

\---

\### ƒ GetComponents

\`\`\`lua

GameObject.GetComponents()

\`\`\`

\*\*Return:\*\* \`Component\[\]\`

\*\*Description:\*\* Возвращает список ВСЕХ компонентов на этом объекте.

\---

\### ƒ GetComponentsInChildren

\`\`\`lua

GameObject.GetComponentsInChildren(name)

\`\`\`

\*\*Return:\*\* \`Component\[\]\`

\*\*Description:\*\* Возвращает Components In Children из GameObject.

\---

\### ƒ GetDamageSystem

\`\`\`lua

GameObject.GetDamageSystem()

\`\`\`

\*\*Return:\*\* \`DamageSystem\`

\*\*Description:\*\* Получает компонент DamageSystem.

\---

\### ƒ GetGoreDollMaster

\`\`\`lua

GameObject.GetGoreDollMaster()

\`\`\`

\*\*Return:\*\* \`GoreDollMaster\`

\*\*Description:\*\* Возвращает скрипт управления, если это NPC или Рэгдолл.

\---

\### p InstantiateLocal

\`\`\`lua

GameObject.InstantiateLocal

\`\`\`

\*\*Return:\*\* \`GameObject\`

\*\*Description:\*\* Создает объект локально (только для этого клиента), без синхронизации по сети.

\---

\### ƒ GetSpawnPath

\`\`\`lua

GameObject.GetSpawnPath()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает строковый путь (Asset Path), по которому этот объект был создан (если он был создан через Instantiate).

\---

\### ƒ GetComponentsInParent

\`\`\`lua

GameObject.GetComponentsInParent(type)

\`\`\`

\*\*Return:\*\* \`Component\[\]\`

\*\*Description:\*\* Ищет компоненты указанного типа в родителях и на основном обьекте (вверх по иерархии).

\---

\### ƒ AddEventListener

\`\`\`lua

GameObject.AddEventListener()

\`\`\`

\*\*Return:\*\* \`EventListener\`

\*\*Description:\*\* Добавляет на обьект EventListener. Используется для обработки евентов OnCollisionEnter и прочее

\---

\### ƒ RemoveEventListener

\`\`\`lua

GameObject.RemoveEventListener()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Удаляет EventListener с обьекта

\---

\### ƒ HaveEventListener

\`\`\`lua

GameObject.HaveEventListener()

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* У обьекта уже есть EventListener?

\---

\### ƒ GetComponentInParent

\`\`\`lua

GameObject.GetComponentInParent()

\`\`\`

\*\*Return:\*\* \`Component\`

\*\*Description:\*\* Ищет компонент указанного типа в родителях и на основном обьекте (вверх по иерархии).

\---

\### ƒ DestroyLocal

\`\`\`lua

GameObject.DestroyLocal()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Удаляет проп локально(не для сетевого кода)

\---

\### ƒ RPC

\`\`\`lua

GameObject.RPC(methodName, playerTarget, {a, b, ...})

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывает RPC у обьекта если он является сетевым обьектом

\---

\## 📦 GoreDollMaster

\### p Host

\`\`\`lua

GoreDollMaster.Host

\`\`\`

\*\*Return:\*\* \`GameObject\`

\*\*Description:\*\* Ссылка на главный GameObject, представляющий этого NPC/Рэгдолла.

\---

\### p Condition

\`\`\`lua

GoreDollMaster.Condition

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Общее физическое состояние/целостность NPC.

\---

\### p Dizzyness

\`\`\`lua

GoreDollMaster.Dizzyness

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Значение оглушения. Сильное головокружение вызывает спотыкание или падение.

\---

\### p Resistance

\`\`\`lua

GoreDollMaster.Resistance

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Множитель урона (0.0 = Иммунитет, 1.0 = Полный урон).

\---

\### p Crawling

\`\`\`lua

GoreDollMaster.Crawling

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* True, если NPC слишком ранен, чтобы ходить, и ползет.

\---

\### p Paralyzed

\`\`\`lua

GoreDollMaster.Paralyzed

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* True, если NPC вообще не может двигаться.

\---

\### p BrainDamage

\`\`\`lua

GoreDollMaster.BrainDamage

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* True, если есть травма головы (меняет поведение ИИ).

\---

\### p Hurt

\`\`\`lua

GoreDollMaster.Hurt

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* True, если NPC в данный момент реагирует на боль.

\---

\### p Mute

\`\`\`lua

GoreDollMaster.Mute

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Если true, отключает голосовые звуки (крики, разговоры).

\---

\### p Infected

\`\`\`lua

GoreDollMaster.Infected

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Если true, применяет визуальные эффекты заражения и черты зомби.

\---

\### p Blood

\`\`\`lua

GoreDollMaster.Blood

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Процент оставшейся крови (0-100). Мало крови ведет к потере сознания.

\---

\### p Team

\`\`\`lua

GoreDollMaster.Team

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Идентификатор команды. NPC-союзники обычно имеют то же имя команды, что и игрок.

\---

\### ƒ TakeDamage

\`\`\`lua

GoreDollMaster.TakeDamage(limb, damage, bldMultiper, dismember)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Наносит урон конкретной конечности. Аргументы: ИмяКости, Урон, Множ.Крови, Расчленение.

\---

\### ƒ TakeBrainDamage

\`\`\`lua

GoreDollMaster.TakeBrainDamage()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Наносит мгновенную травму мозга.

\---

\### ƒ StopHeartFunctions

\`\`\`lua

GoreDollMaster.StopHeartFunctions()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывает мгновенную смерть от остановки сердца.

\---

\### ƒ StopBrainFunctions

\`\`\`lua

GoreDollMaster.StopBrainFunctions()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вызывает мгновенную смерть от отказа мозга.

\---

\### ƒ SetRandomScale

\`\`\`lua

GoreDollMaster.SetRandomScale()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Применяет случайные пропорции тела к NPC.

\---

\### ƒ AssignRandomSkin

\`\`\`lua

GoreDollMaster.AssignRandomSkin()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Рандомизирует одежду и текстуру кожи.

\---

\### ƒ Choke

\`\`\`lua

GoreDollMaster.Choke()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Выполняет удушение, отправляя NPC в бессознательное состояние.

\---

\### ƒ Knockout

\`\`\`lua

GoreDollMaster.Knockout()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Отправляет NPC в глубокий нокаут.

\---

\### ƒ KnockoutTimed

\`\`\`lua

GoreDollMaster.KnockoutTimed(time)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Отправляет NPC в нокаут на указанное количество секунд.

\---

\### ƒ WakeUp

\`\`\`lua

GoreDollMaster.WakeUp()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Приводит NPC в чувство из бессознательного состояния.

\---

\### ƒ DropWeapon

\`\`\`lua

GoreDollMaster.DropWeapon()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Заставляет NPC бросить экипированное оружие.

\---

\## 📦 GUI

\### ƒ GetColor

\`\`\`lua

GUI.GetColor()

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Возвращает текущий глобальный цвет тонировки всех элементов интерфейса.

\---

\### ƒ SetColor

\`\`\`lua

GUI.SetColor(c)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Устанавливает глобальный цвет тонировки. Все последующие элементы будут окрашены в этот цвет.

\---

\### ƒ GetBackgroundColor

\`\`\`lua

GUI.GetBackgroundColor()

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Возвращает текущий цвет фона.

\---

\### ƒ SetBackgroundColor

\`\`\`lua

GUI.SetBackgroundColor(c)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Устанавливает цвет фона для таких элементов, как Кнопки и Панели.

\---

\### ƒ GetContentColor

\`\`\`lua

GUI.GetContentColor()

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Возвращает текущий цвет текста или изображений.

\---

\### ƒ SetContentColor

\`\`\`lua

GUI.SetContentColor(c)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Устанавливает цвет для текста и изображений внутри элементов интерфейса.

\---

\### ƒ ResetColors

\`\`\`lua

GUI.ResetColors()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Сбрасывает все цвета интерфейса (Тон, Фон, Контент) обратно к белому стандарту.

\---

\### ƒ ButtonRect

\`\`\`lua

GUI.ButtonRect(rect, label, style)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Рисует кнопку в точных координатах (x, y, ширина, высота). Возвращает true при клике.

\---

\### ƒ ButtonRectTexture

\`\`\`lua

GUI.ButtonRectTexture(rect, tex, style)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Рисует кнопку с картинкой вместо текста в указанной позиции.

\---

\### ƒ RepeatButtonRect

\`\`\`lua

GUI.RepeatButtonRect(rect, label, style)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Рисует кнопку, которая возвращает true каждый кадр при удержании (в указанной позиции).

\---

\### ƒ Box

\`\`\`lua

GUI.Box(rect, label, style)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Рисует фоновую панель/коробку позади других элементов.

\---

\### ƒ LabelRect

\`\`\`lua

GUI.LabelRect(rect, label, style)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Рисует текстовую метку в точных пиксельных координатах.

\---

\### ƒ DrawTexture

\`\`\`lua

GUI.DrawTexture(rect, tex, scaleMode, alphaBlend, imageAspect)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Рисует изображение (Texture2D) на экране в указанных координатах.

\---

\### ƒ ToggleRect

\`\`\`lua

GUI.ToggleRect(rect, value, label, style)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Рисует переключатель (галочку) в точных координатах. Возвращает новое состояние (true/false).

\---

\### ƒ Button

\`\`\`lua

GUI.Button(label, width, height, style)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Рисует кнопку с авто-размещением. Использовать внутри Горизонтальных/Вертикальных групп или Областей.

\---

\### ƒ RepeatButton

\`\`\`lua

GUI.RepeatButton(label, width, height, style)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Рисует кнопку (авто-размещение), которая выполняется непрерывно, пока зажата.

\---

\### ƒ Toggle

\`\`\`lua

GUI.Toggle(value, label, width, height, style)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Рисует чекбокс (Вкл/Выкл) с авто-размещением. Возвращает true, если включен.

\---

\### ƒ Label

\`\`\`lua

GUI.Label(label, width, height, style)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Рисует текст. Поддерживает теги форматирования (цвет, размер, жирный).

\---

\### ƒ TextField

\`\`\`lua

GUI.TextField(text, maxLength, width, height, style)

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Рисует однострочное поле ввода. Возвращает измененную строку.

\---

\### ƒ PasswordField

\`\`\`lua

GUI.PasswordField(password, maskChar, maxLength, width, height, style)

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Рисует поле ввода, скрывающее символы (например, звездочками '\*').

\---

\### ƒ TextArea

\`\`\`lua

GUI.TextArea(text, maxLength, width, height, style)

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Рисует многострочное поле ввода. Полезно для больших текстов.

\---

\### ƒ HorizontalSlider

\`\`\`lua

GUI.HorizontalSlider(value, leftValue, rightValue, width, height)

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Рисует горизонтальный ползунок для выбора значения между минимумом и максимумом.

\---

\### ƒ VerticalSlider

\`\`\`lua

GUI.VerticalSlider(value, topValue, bottomValue, width, height)

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Рисует вертикальный ползунок.

\---

\### ƒ SliderRect

\`\`\`lua

GUI.SliderRect(rect, value, leftValue, rightValue)

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Рисует ползунок в точных пиксельных координатах.

\---

\### ƒ GetLastRect

\`\`\`lua

GUI.GetLastRect()

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Возвращает прямоугольник (позицию/размер) последнего нарисованного элемента. Для подсказок.

\---

\### ƒ BeginArea

\`\`\`lua

GUI.BeginArea(rect)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Создает область отсечения. Координаты элементов внутри считаются относительно этой области.

\---

\### ƒ EndArea

\`\`\`lua

GUI.EndArea()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Завершает текущий блок Area.

\---

\### ƒ BeginHorizontal

\`\`\`lua

GUI.BeginHorizontal()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Начинает горизонтальную группу. Элементы размещаются бок о бок.

\---

\### ƒ EndHorizontal

\`\`\`lua

GUI.EndHorizontal()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Завершает горизонтальную группу.

\---

\### ƒ BeginVertical

\`\`\`lua

GUI.BeginVertical()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Начинает вертикальную группу. Элементы размещаются сверху вниз.

\---

\### ƒ EndVertical

\`\`\`lua

GUI.EndVertical()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Завершает вертикальную группу.

\---

\### ƒ BeginScrollView

\`\`\`lua

GUI.BeginScrollView(scrollPos, width, height)

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* Создает область с прокруткой. Нужно, если контент не влезает на экран.

\---

\### ƒ EndScrollView

\`\`\`lua

GUI.EndScrollView()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Завершает область прокрутки.

\---

\### ƒ Space

\`\`\`lua

GUI.Space(pixels)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вставляет пустое пространство в X пикселей между элементами.

\---

\### ƒ FlexibleSpace

\`\`\`lua

GUI.FlexibleSpace()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Вставляет резиновый отступ, который расталкивает элементы, заполняя место.

\---

\### ƒ Separator

\`\`\`lua

GUI.Separator()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Рисует горизонтальную линию для разделения секций.

\---

\### ƒ NewStyle

\`\`\`lua

GUI.NewStyle()

\`\`\`

\*\*Return:\*\* \`GUIStyle\`

\*\*Description:\*\* Создает объект GUIStyle для настройки шрифтов, цветов и выравнивания.

\---

\### ƒ DrawLine

\`\`\`lua

GUI.DrawLine(start, end, color, width)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Рисует цветную линию между двумя точками на экране.

\---

\## 📦 Importer

\### ƒ ImportTexture

\`\`\`lua

Importer.ImportTexture(path)

\`\`\`

\*\*Return:\*\* \`Texture\`

\*\*Description:\*\* Загружает изображение (.png, .jpg) из папки мода и возвращает его как объект Texture2D.

\---

\### ƒ ImportAudioClip

\`\`\`lua

Importer.ImportAudioClip(path)

\`\`\`

\*\*Return:\*\* \`AudioClip\`

\*\*Description:\*\* Загружает аудиофайл (.mp3, .wav, .ogg) из папки мода и возвращает его как AudioClip.

\---

\### p LoadGameObjectFromAssetBundle

\`\`\`lua

Importer.LoadGameObjectFromAssetBundle

\`\`\`

\*\*Return:\*\* \`GameObject\`

\*\*Description:\*\* Загружает GameObject (префаб) из внешнего файла AssetBundle.

\---

\### p LoadMaterialFromAssetBundle

\`\`\`lua

Importer.LoadMaterialFromAssetBundle

\`\`\`

\*\*Return:\*\* \`Material\`

\*\*Description:\*\* Загружает материал из AssetBundle.

\---

\### p LoadTextureFromAssetBundle

\`\`\`lua

Importer.LoadTextureFromAssetBundle

\`\`\`

\*\*Return:\*\* \`Texture\`

\*\*Description:\*\* Загружает текстуру из AssetBundle.

\---

\### p LoadSpriteFromAssetBundle

\`\`\`lua

Importer.LoadSpriteFromAssetBundle

\`\`\`

\*\*Return:\*\* \`Sprite\`

\*\*Description:\*\* Загружает спрайт из AssetBundle.

\---

\### p LoadMeshFromAssetBundle

\`\`\`lua

Importer.LoadMeshFromAssetBundle

\`\`\`

\*\*Return:\*\* \`Mesh\`

\*\*Description:\*\* Загружает 3D-модель (Mesh) из AssetBundle.

\---

\### p LoadSceneFromAssetBundle

\`\`\`lua

Importer.LoadSceneFromAssetBundle

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Загружает сцену (уровень) из AssetBundle. Осторожно: может сменить текущую карту.

\---

\### ƒ ImportModel

\`\`\`lua

Importer.ImportModel(path, format, collider)

\`\`\`

\*\*Return:\*\* \`GameObject\`

\*\*Description:\*\* Загружает 3D-модель (.obj) из папки мода. 'AddMeshCollider' создает физические коллизии для неё.

\---

\### ƒ CreateTexture

\`\`\`lua

Importer.CreateTexture(width, height)

\`\`\`

\*\*Return:\*\* \`Texture\`

\*\*Description:\*\* Создает новую, пустую текстуру (Texture2D) с указанной шириной и высотой.

\---

\### ƒ LoadShaderFromAssetBundle

\`\`\`lua

Importer.LoadShaderFromAssetBundle(bundlePath, assetName)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Загружает заранее скомпилированный шейдер из AssetBundle(не рекомендуется использовать здесь)

\---

\## 📦 Input

\### p LockedMouse

\`\`\`lua

Input.LockedMouse

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Свойство для блокировки курсора. True = режим шутера (скрыт), False = режим меню (виден).

\---

\### ƒ GetKeyDown

\`\`\`lua

Input.GetKeyDown(key)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Возвращает true только в тот кадр, когда клавиша была нажата.

\*\*Example:\*\*

\`\`\`lua

function Update()

if Input.GetKeyDown("Space") then Main.SendChatMessageLocal("Нажат пробел (Прыжок)!") end
end

\`\`\`

\---

\### ƒ GetKeyUp

\`\`\`lua

Input.GetKeyUp(key)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Возвращает true только в тот кадр, когда клавиша была отпущена.

\---

\### ƒ GetKey

\`\`\`lua

Input.GetKey(key)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Возвращает true всё время, пока клавиша удерживается.

\---

\### ƒ GetButtonDown

\`\`\`lua

Input.GetButtonDown(button)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет нажатие кнопки из Unity Input Manager (напр., 'Fire1', 'Jump') в текущем кадре.

\---

\### ƒ GetButtonUp

\`\`\`lua

Input.GetButtonUp(button)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет отпускание кнопки из Unity Input Manager в текущем кадре.

\---

\### ƒ GetButton

\`\`\`lua

Input.GetButton(button)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет, удерживается ли кнопка из Unity Input Manager.

\---

\### ƒ SetButton

\`\`\`lua

Input.SetButton(button, pressed)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Эмулирует нажатие или отпускание кнопки через скрипт. Полезно для виртуального управления.

\---

\### ƒ GetPressedKeys

\`\`\`lua

Input.GetPressedKeys()

\`\`\`

\*\*Return:\*\* \`List\`

\*\*Description:\*\* Возвращает список имен всех клавиш, которые удерживаются в данный момент.

\---

\### ƒ GetPressedButtons

\`\`\`lua

Input.GetPressedButtons()

\`\`\`

\*\*Return:\*\* \`List\`

\*\*Description:\*\* Возвращает список всех кнопок Unity (Fire1, Jump и т.д.), удерживаемых сейчас.

\---

\### ƒ GetScreenRect

\`\`\`lua

Input.GetScreenRect()

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* Возвращает текущее разрешение экрана как Vector2 (Ширина, Высота).

\---

\### ƒ GetMousePosition

\`\`\`lua

Input.GetMousePosition()

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* Возвращает пиксельные координаты курсора мыши на экране.

\---

\### ƒ GetAxis

\`\`\`lua

Input.GetAxis(axis)

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Возвращает значение от -1 до 1 для оси ввода (напр., 'Horizontal', 'Mouse X').

\---

\### ƒ GetMouseDown

\`\`\`lua

Input.GetMouseDown(button)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Возвращает true, если кнопка мыши (0=ЛКМ, 1=ПКМ, 2=СКМ) была нажата в этом кадре.

\---

\### ƒ GetMouseUp

\`\`\`lua

Input.GetMouseUp(button)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Возвращает true, если кнопка мыши была отпущена в этом кадре.

\---

\### ƒ GetMouse

\`\`\`lua

Input.GetMouse(button)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Возвращает true, пока кнопка мыши удерживается.

\---

\### ƒ GetTouchCount

\`\`\`lua

Input.GetTouchCount()

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Возвращает кол-во касаний на экран

\---

\### ƒ GetTouch

\`\`\`lua

Input.GetTouch(index)

\`\`\`

\*\*Return:\*\* \`InputTouchInfo\`

\*\*Description:\*\* Получает касание по экрану по индексу

\---

\### ƒ GetDeviceAttitude

\`\`\`lua

Input.GetDeviceAttitude()

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Возвращает Device Attitude из Input.

\---

\### ƒ GetDeviceGravity

\`\`\`lua

Input.GetDeviceGravity()

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Возвращает Device Gravity из Input.

\---

\### ƒ GetDeviceAcceleration

\`\`\`lua

Input.GetDeviceAcceleration()

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Возвращает Device Acceleration из Input.

\---

\### ƒ GetRotationRate

\`\`\`lua

Input.GetRotationRate()

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Возвращает Rotation Rate из Input.

\---

\### p GyroscopeEnabled

\`\`\`lua

Input.GyroscopeEnabled

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Доступ к свойству GyroscopeEnabled класса Input.

\---

\### ƒ GetGyroscopeSupported

\`\`\`lua

Input.GetGyroscopeSupported()

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Возвращает Gyroscope Supported из Input.

\---

\### ƒ GetDeviceInfo

\`\`\`lua

Input.GetDeviceInfo()

\`\`\`

\*\*Return:\*\* \`DynValue\`

\*\*Description:\*\* Возвращает Device Info из Input.

\---

\### ƒ GetAcceleration

\`\`\`lua

Input.GetAcceleration()

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Возвращает Acceleration из Input.

\---

\## 📦 InputTouchInfo

\### p Began

\`\`\`lua

InputTouchInfo.Began

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Началось ли нажатие?

\---

\### p Moved

\`\`\`lua

InputTouchInfo.Moved

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Передвинулось ли касание?

\---

\### p Ended

\`\`\`lua

InputTouchInfo.Ended

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Касание закончилось?

\---

\### p Position

\`\`\`lua

InputTouchInfo.Position

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* Позиция касания

\---

\## 📦 JSON

\### p parse

\`\`\`lua

JSON.parse

\`\`\`

\*\*Return:\*\* \`table\`

\*\*Description:\*\* Преобразует строку JSON в Lua-таблицу.

\---

\### p serialize

\`\`\`lua

JSON.serialize

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Преобразует Lua-таблицу в строку JSON.

\---

\## 📦 LayerMask

\### ƒ New

\`\`\`lua

LayerMask.New(maskValue)

\`\`\`

\*\*Return:\*\* \`LayerMask\`

\*\*Description:\*\* Создает LayerMask из битовой маски (числа).

\---

\### p value

\`\`\`lua

LayerMask.value

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Сырое числовое значение маски.

\---

\### ƒ ToLayerMask

\`\`\`lua

LayerMask.ToLayerMask()

\`\`\`

\*\*Return:\*\* \`LayerMask\`

\*\*Description:\*\* Возвращает маску, которая попадает во ВСЁ.

\---

\### ƒ FromName

\`\`\`lua

LayerMask.FromName(layerName)

\`\`\`

\*\*Return:\*\* \`LayerMask\`

\*\*Description:\*\* Создает маску для одного имени слоя.

\---

\### ƒ FromNames

\`\`\`lua

LayerMask.FromNames(layerNames)

\`\`\`

\*\*Return:\*\* \`LayerMask\`

\*\*Description:\*\* Создает маску из нескольких имен слоев.

\---

\### ƒ ContainsLayer

\`\`\`lua

LayerMask.ContainsLayer(layer)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет, включает ли маска ID слоя.

\---

\### ƒ AddLayer

\`\`\`lua

LayerMask.AddLayer(layer)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Добавляет ID слоя в маску.

\---

\### ƒ RemoveLayer

\`\`\`lua

LayerMask.RemoveLayer(layer)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Удаляет ID слоя из маски.

\---

\### ƒ Invert

\`\`\`lua

LayerMask.Invert()

\`\`\`

\*\*Return:\*\* \`LayerMask\`

\*\*Description:\*\* Возвращает маску со всем, чего НЕТ в текущей.

\---

\### ƒ Combine

\`\`\`lua

LayerMask.Combine(other)

\`\`\`

\*\*Return:\*\* \`LayerMask\`

\*\*Description:\*\* Объединяет две маски.

\---

\### ƒ Intersect

\`\`\`lua

LayerMask.Intersect(other)

\`\`\`

\*\*Return:\*\* \`LayerMask\`

\*\*Description:\*\* Возвращает общие слои двух масок.

\---

\### ƒ GetLayerIndexByName

\`\`\`lua

LayerMask.GetLayerIndexByName(layerName)

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Возвращает числовой ID слоя по имени.

\---

\## 📦 Main

\### ƒ SendServerEvent

\`\`\`lua

Main.SendServerEvent(data(string))

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Отправляет модовое сообщение на все модлоадеры. Обрабатывается евентом OnGetRPC

\*\*Example:\*\*

\`\`\`lua

function OnGetRPC(data)

Main.SendChatMessageLocal("Data: " .. data)
end

function OnRC2Spawn(objTransform)

Main.SendServerEvent("pl=" .. Player.GetLocal().GetID() .. "n:" .. objTransform.GameObject.Name)
end

\`\`\`

\---

\### ƒ SendAnnouncement

\`\`\`lua

Main.SendAnnouncement(header, content, player)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Отображает большое объявление на экране конкретного игрока.

\---

\### ƒ SendRules

\`\`\`lua

Main.SendRules(ActionCam, BanAIGoreDolls, BanBigExplosives, BanClothes, BanGoreDolls, BanEntities, BanExplosives, BanExplosiveWeapons, BanFood, BanHeavyWeapons, BanLightWeapons, BanMedicine, BanMeleeWeapons, BanNextbots, BanProps, BanRealityCrusher, BanVehicles, CanDropWeapons, dropAllInventoryItemsOnDie, CreatorMode, FriendlyFire, HostBadge, HostSwitchFeed, IgnoredByAI, InfiniteAmmo, InfiniteStamina, Invincibility, KillFeed, NoClip, PlayerConnectionFeed, SlowMo, SpawnAsInfected, DisableFists, DisableKicks, KeepInventory, RespawnPenalty, CloseServerOnDisconnec, CanLoadSaves, AllowViceHos, AllowChangesByViceHos, AllowGrab)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Обновляет правила сервера (баны, настройки) для ВСЕХ игроков. Требует длинный список аргументов.

\---

\### ƒ SendRulesToPlayer

\`\`\`lua

Main.SendRulesToPlayer(targetPlayer, ActionCam, BanAIGoreDolls, BanBigExplosives, BanClothes, BanGoreDolls, BanEntities, BanExplosives, BanExplosiveWeapons, BanFood, BanHeavyWeapons, BanLightWeapons, BanMedicine, BanMeleeWeapons, BanNextbots, BanProps, BanRealityCrusher, BanVehicles, CanDropWeapons, dropAllInventoryItemsOnDie, CreatorMode, FriendlyFire, HostBadge, HostSwitchFeed, IgnoredByAI, InfiniteAmmo, InfiniteStamina, Invincibility, KillFeed, NoClip, PlayerConnectionFeed, SlowMo, SpawnAsInfected, DisableFists, DisableKicks, KeepInventory, RespawnPenalty, CloseServerOnDisconnec, CanLoadSaves, AllowViceHos, AllowChangesByViceHos, AllowGrab)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Обновляет правила сервера для ОДНОГО конкретного игрока.

\---

\### ƒ GenerateNavMesh

\`\`\`lua

Main.GenerateNavMesh()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Принудительно пересчитывает навигационную сетку (NavMesh). Вызывайте после спавна стен или зданий, чтобы NPC видели препятствия.

\---

\### ƒ GetCurrentScene

\`\`\`lua

Main.GetCurrentScene()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает название текущей загруженной карты (например, 'Legacy', 'Polar6').

\---

\### ƒ GetCurrentPlatform

\`\`\`lua

Main.GetCurrentPlatform()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает платформу устройства: 'Android' или 'PC'. Полезно для оптимизации модов под телефоны.

\---

\### ƒ LoadScene

\`\`\`lua

Main.LoadScene(sceneName)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Мгновенно загружает новую карту. Внимание: это сбрасывает состояние игры и отключает игроков в мультиплеере.

\*\*Example:\*\*

\`\`\`lua

function Start()

-- Загрузка карты (Внимание: Перезагружает игру) Main.LoadScene("map_legacy")
end

\`\`\`

\---

\### ƒ Log

\`\`\`lua

Main.Log(msg)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Выводит стандартное белое сообщение в консоль отладки (клавиша Insert).

\---

\### ƒ LogError

\`\`\`lua

Main.LogError(msg)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Выводит красное сообщение об ошибке в консоль. Используйте для критических сбоев.

\---

\### p SetObjective

\`\`\`lua

Main.SetObjective

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Устанавливает текст текущей задачи. Если указан Player, задача меняется только для него.

\---

\### p SetTimer

\`\`\`lua

Main.SetTimer

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Устанавливает таймер. Если указан Player, таймер меняется только для него.

\---

\### p SetTitle

\`\`\`lua

Main.SetTitle

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Показывает заголовок на экране. Если указан Player, показывает только ему.

\---

\### ƒ SendChatMessageLocal

\`\`\`lua

Main.SendChatMessageLocal(msg)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Отправляет сообщение в чат, видимое ТОЛЬКО вам. Идеально для системных уведомлений.

\---

\### ƒ SendChatMessage

\`\`\`lua

Main.SendChatMessage(msg)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Отправляет сообщение в общий чат, которое видят все игроки на сервере.

\---

\### ƒ SendChatMessageError

\`\`\`lua

Main.SendChatMessageError(msg)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Отправляет красное сообщение об ошибке в локальный чат. Полезно для реакции на неверные команды.

\---

\### ƒ SetConsoleVisible

\`\`\`lua

Main.SetConsoleVisible(visible)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Программно открывает или закрывает окно внутриигровой консоли отладки.

\---

\### ƒ InMultiplayer

\`\`\`lua

Main.InMultiplayer()

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Возвращает true, если игра в данный момент находится в мультиплеерном режиме.

\---

\### ƒ AllocateViewID

\`\`\`lua

Main.AllocateViewID(photonView(component))

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Регистрирует созданый вами photonView. Используется только в редких случаях

\*\*Example:\*\*

\`\`\`lua

function CreatePUNObject(name)

local \\\_go = GameObject.Create(name) if \\\_go == nil or not \\\_go.IsValid() then return nil end local \\\_pv = \\\_go.AddComponent("PhotonView") if \\\_pv == nil then return nil end Main.AllocateViewID(\\\_pv) return \\\_go
end

\`\`\`

\---

\## 📦 Material

\### p mat

\`\`\`lua

Material.mat

\`\`\`

\*\*Return:\*\* \`Material\`

\*\*Description:\*\* Внутренняя ссылка на нативный Unity Material.

\---

\### p color

\`\`\`lua

Material.color

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Основной базовый цвет (Альбедо) материала.

\---

\### p mainTexture

\`\`\`lua

Material.mainTexture

\`\`\`

\*\*Return:\*\* \`Texture\`

\*\*Description:\*\* Основная текстура. Перекрывает цвет, если установлена.

\---

\### p metallic

\`\`\`lua

Material.metallic

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Насколько поверхность металлическая (0=Пластик, 1=Металл).

\---

\### p smoothness

\`\`\`lua

Material.smoothness

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Насколько поверхность гладкая (0=Шершавая/Матовая, 1=Полированная/Зеркало).

\---

\### p normalMap

\`\`\`lua

Material.normalMap

\`\`\`

\*\*Return:\*\* \`Texture\`

\*\*Description:\*\* Текстура (карта нормалей), добавляющая рельеф поверхности.

\---

\### p emissionColor

\`\`\`lua

Material.emissionColor

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Цвет свечения материала. Черный = Нет свечения.

\---

\### p emissionMap

\`\`\`lua

Material.emissionMap

\`\`\`

\*\*Return:\*\* \`Texture\`

\*\*Description:\*\* Текстура, определяющая, какие части объекта светятся.

\---

\### p transparent

\`\`\`lua

Material.transparent

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Если true, включает прозрачность (стекло, призраки).

\---

\### p shader

\`\`\`lua

Material.shader

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Имя шейдера, используемого материалом.

\---

\### ƒ Create

\`\`\`lua

Material.Create(shaderName)

\`\`\`

\*\*Return:\*\* \`Material\`

\*\*Description:\*\* Создает новый Материал, используя шейдер 'Standard'.

\---

\### ƒ SetFloatProperty

\`\`\`lua

Material.SetFloatProperty(name, propertyVal)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Задает значение шейдера если он есть

\---

\### ƒ GetFloatProperty

\`\`\`lua

Material.GetFloatProperty(name)

\`\`\`

\*\*Return:\*\* \`var\`

\*\*Description:\*\* Возвращает значение переменной шейдера

\---

\### ƒ SetColorProperty

\`\`\`lua

Material.SetColorProperty(name, propertyVal)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Задает значение шейдера если он есть

\---

\### ƒ GetColorProperty

\`\`\`lua

Material.GetColorProperty(name)

\`\`\`

\*\*Return:\*\* \`var\`

\*\*Description:\*\* Возвращает значение переменной шейдера

\---

\### ƒ SetVectorProperty

\`\`\`lua

Material.SetVectorProperty(name, propertyVal)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Задает значение шейдера если он есть

\---

\### ƒ GetVectorProperty

\`\`\`lua

Material.GetVectorProperty(name)

\`\`\`

\*\*Return:\*\* \`var\`

\*\*Description:\*\* Возвращает значение переменной шейдера

\---

\### ƒ SetTextureProperty

\`\`\`lua

Material.SetTextureProperty(name, propertyVal)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Задает значение шейдера если он есть

\---

\### ƒ GetTextureProperty

\`\`\`lua

Material.GetTextureProperty(name)

\`\`\`

\*\*Return:\*\* \`var\`

\*\*Description:\*\* Возвращает значение переменной шейдера

\---

\### ƒ GetAllShaderProperties

\`\`\`lua

Material.GetAllShaderProperties()

\`\`\`

\*\*Return:\*\* \`string\[\]\`

\*\*Description:\*\* Возвращает все параметры шейдера(если он есть)

\---

\### ƒ EnableKeyword

\`\`\`lua

Material.EnableKeyword(keyword)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Включает keyword шейдера

\---

\### ƒ DisableKeyword

\`\`\`lua

Material.DisableKeyword(keyword)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Выключает keyword шейдера

\---

\### ƒ IsKeywordEnabled

\`\`\`lua

Material.IsKeywordEnabled()

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Возвращает значение переменной шейдера(включен ли keyword)

\---

\### ƒ GetTag

\`\`\`lua

Material.GetTag(tag, currentRenderer(bool))

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает тег шейдера

\---

\### ƒ SetOverrideTag

\`\`\`lua

Material.SetOverrideTag(tag, value(string))

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Ставит Override тег шейдеру/рендереру

\---

\### ƒ SetShaderFromAssetBundle

\`\`\`lua

Material.SetShaderFromAssetBundle(bundlePath, assetName)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Задает заранее скомпилированный шейдер(AssetBundle) на материал

\---

\## 📦 Matrix4x4

\### ƒ New

\`\`\`lua

Matrix4x4.New(row0, row1, row2, row3)

\`\`\`

\*\*Return:\*\* \`Matrix4x4\`

\*\*Description:\*\* Создает матрицу трансформации 4x4 вручную.

\---

\### ƒ ToMatrix4x4

\`\`\`lua

Matrix4x4.ToMatrix4x4()

\`\`\`

\*\*Return:\*\* \`Matrix4x4\`

\*\*Description:\*\* Преобразует совместимый объект в Matrix4x4.

\---

\### ƒ Identity

\`\`\`lua

Matrix4x4.Identity()

\`\`\`

\*\*Return:\*\* \`Matrix4x4\`

\*\*Description:\*\* Стандартная матрица (Позиция 0, Вращение 0, Масштаб 1). Ничего не меняет при умножении.

\---

\### ƒ Add

\`\`\`lua

Matrix4x4.Add(other)

\`\`\`

\*\*Return:\*\* \`Matrix4x4\`

\*\*Description:\*\* Складывает две матрицы поэлементно.

\---

\### ƒ Sub

\`\`\`lua

Matrix4x4.Sub(other)

\`\`\`

\*\*Return:\*\* \`Matrix4x4\`

\*\*Description:\*\* Вычитает одну матрицу из другой.

\---

\### ƒ Mul

\`\`\`lua

Matrix4x4.Mul(scalar)

\`\`\`

\*\*Return:\*\* \`Matrix4x4\`

\*\*Description:\*\* Умножает матрицу на скалярное число.

\---

\### ƒ MultiplyVector

\`\`\`lua

Matrix4x4.MultiplyVector(v)

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Трансформирует направление (Vector3), учитывая только вращение (игнорирует позицию).

\---

\### ƒ MultiplyPoint

\`\`\`lua

Matrix4x4.MultiplyPoint(v)

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Трансформирует позицию (Vector3) из одной системы координат в другую.

\---

\### ƒ TRS

\`\`\`lua

Matrix4x4.TRS(position, rotation, scale)

\`\`\`

\*\*Return:\*\* \`Matrix4x4\`

\*\*Description:\*\* Создает матрицу из Позиции, Вращения и Масштаба. Используется для конвертации координат.

\---

\### p m00

\`\`\`lua

Matrix4x4.m00

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Значение ячейки матрицы (ряд 0, кол 0).

\---

\## 📦 Mesh

\### ƒ New

\`\`\`lua

Mesh.New(umesh)

\`\`\`

\*\*Return:\*\* \`Mesh\`

\*\*Description:\*\* Создает новый пустой Mesh объект для процедурной генерации.

\---

\### ƒ GetFromUnity

\`\`\`lua

Mesh.GetFromUnity(mesh)

\`\`\`

\*\*Return:\*\* \`Mesh\`

\*\*Description:\*\* Копирует данные меша из существующего Unity Mesh.

\---

\### p mesh

\`\`\`lua

Mesh.mesh

\`\`\`

\*\*Return:\*\* \`Mesh\`

\*\*Description:\*\* Внутренняя ссылка на нативный объект Unity Mesh.

\---

\### ƒ Name

\`\`\`lua

Mesh.Name()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Имя меш-ассета.

\---

\### ƒ VertexCount

\`\`\`lua

Mesh.VertexCount()

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Общее количество вершин (точек) в модели.

\---

\### ƒ SubMeshCount

\`\`\`lua

Mesh.SubMeshCount()

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Количество под-мешей. Каждый под-меш обычно использует свой материал.

\---

\### ƒ GetVertices

\`\`\`lua

Mesh.GetVertices()

\`\`\`

\*\*Return:\*\* \`Vector3\[\]\`

\*\*Description:\*\* Возвращает список позиций вершин (массив Vector3).

\---

\### ƒ GetNormals

\`\`\`lua

Mesh.GetNormals()

\`\`\`

\*\*Return:\*\* \`Vector3\[\]\`

\*\*Description:\*\* Возвращает список нормалей (направление света).

\---

\### ƒ GetUV

\`\`\`lua

Mesh.GetUV()

\`\`\`

\*\*Return:\*\* \`Vector2\[\]\`

\*\*Description:\*\* Возвращает текстурные координаты (массив Vector2).

\---

\### ƒ GetTriangles

\`\`\`lua

Mesh.GetTriangles()

\`\`\`

\*\*Return:\*\* \`int\[\]\`

\*\*Description:\*\* Возвращает список индексов, соединяющих вершины в треугольники.

\---

\### ƒ SetVertices

\`\`\`lua

Mesh.SetVertices(vertices)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Устанавливает позиции вершин. Длина массива определяет количество вершин.

\---

\### ƒ SetNormals

\`\`\`lua

Mesh.SetNormals(normals)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Устанавливает векторы нормалей.

\---

\### ƒ SetUV

\`\`\`lua

Mesh.SetUV(uv)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Устанавливает маппинг текстурных координат.

\---

\### ƒ SetTriangles

\`\`\`lua

Mesh.SetTriangles(triangles)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Устанавливает индексы треугольников. Определяет поверхность формы.

\---

\### ƒ RecalculateNormals

\`\`\`lua

Mesh.RecalculateNormals()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Автоматически рассчитывает сглаженные нормали на основе треугольников.

\---

\### ƒ RecalculateBounds

\`\`\`lua

Mesh.RecalculateBounds()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Обновляет невидимые границы (bounds), используемые для отрисовки и физики.

\---

\### ƒ RecalculateTangents

\`\`\`lua

Mesh.RecalculateTangents()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Рассчитывает тангенсы, необходимые для правильной работы карт нормалей.

\---

\## 📦 PenetrationInfo

\### p penetrated

\`\`\`lua

PenetrationInfo.penetrated

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Было ли соприкосновение?

\---

\### p direction

\`\`\`lua

PenetrationInfo.direction

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Направление соприкосновения

\---

\### p distance

\`\`\`lua

PenetrationInfo.distance

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Дистанция между точками

\---

\## 📦 Physic

\### ƒ Raycast

\`\`\`lua

Physic.Raycast(origin, direction, maxDistance, layerMask, \*queryTriggerInteraction\*)

\`\`\`

\*\*Return:\*\* \`RaycastInfo\`

\*\*Description:\*\* Пускает невидимый луч из точки в указанном направлении. Возвращает true, если он во что-то попал. Аргумент queryTriggerInteraction не обязателен к написанию

\---

\### ƒ RaycastAll

\`\`\`lua

Physic.RaycastAll(origin, direction, maxDistance, layerMask)

\`\`\`

\*\*Return:\*\* \`RaycastInfo\[\]\`

\*\*Description:\*\* Пускает пробивающий луч, который возвращает список ВСЕХ объектов на своем пути. Аргумент queryTriggerInteraction не обязателен

\---

\### ƒ OverlapSphere

\`\`\`lua

Physic.OverlapSphere(origin, radius, layerMask, \*queryTriggerInteraction)

\`\`\`

\*\*Return:\*\* \`Transform\[\]\`

\*\*Description:\*\* Проверяет сферическую область на наличие коллайдеров. Полезно для взрывов или урона по площади. Аргумент queryTriggerInteraction не обязателен

\---

\### p Gravity

\`\`\`lua

Physic.Gravity

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Сила гравитации физического движка

\---

\### ƒ IgnoreCollision

\`\`\`lua

Physic.IgnoreCollision(Component(colliderA), Component(colliderB), ignoreCollision)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Игнорировать коллизии между обьектами

\*\*Example:\*\*

\`\`\`lua

Main.IgnoreCollision(collA, collB, false)

\`\`\`

\---

\### ƒ Linecast

\`\`\`lua

Physic.Linecast(startPos, endPos, layerMask)

\`\`\`

\*\*Return:\*\* \`RaycastInfo\`

\*\*Description:\*\* Linecast физического модуля. Аргумент queryTriggerInteraction не обязателен

\---

\### ƒ RaycastNonAlloc

\`\`\`lua

Physic.RaycastNonAlloc(origin, direction, maxResults, maxDistance, layerMask,queryTriggerInteraction)

\`\`\`

\*\*Return:\*\* \`RaycastInfo\[\]\`

\*\*Description:\*\* Пускает пробивающий луч, который возвращает список ВСЕХ объектов на своем пути(ограничивается аргументом maxResults). Аргумент queryTriggerInteraction не обязателен

\---

\### ƒ SphereCast

\`\`\`lua

Physic.SphereCast(origin, radius, direction, maxDistance, layerMask)

\`\`\`

\*\*Return:\*\* \`RaycastInfo\`

\*\*Description:\*\* Создает шар и возвращает информацию об первом обьекте внутри его

\---

\### ƒ SphereCastAll

\`\`\`lua

Physic.SphereCastAll(origin, radius, direction, maxDistance, layerMask)

\`\`\`

\*\*Return:\*\* \`RaycastInfo\[\]\`

\*\*Description:\*\* Создает шар и возвращает информацию об обьектах внутри его

\---

\### ƒ CheckSphere

\`\`\`lua

Physic.CheckSphere(position, radius, layerMask, \*queryTriggerInteraction\*)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Создает шар и возвращает результат, было ли осуществлено хоть одно попадание с целями. Аргумент queryTriggerInteraction не обязателен

\---

\### ƒ CheckBox

\`\`\`lua

Physic.CheckBox(center, halfExtents, rotation(Vector4), layerMask, \*queryTriggerInteraction\*)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Создает куб и возвращает результат, было ли осуществлено хоть одно попадание с целями. Аргумент queryTriggerInteraction не обязателен

\---

\### ƒ CheckCapsule

\`\`\`lua

Physic.CheckCapsule(pointA, pointB, radius, layerMask, \*queryTriggerInteraction\*)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Создает капсулу и возвращает результат, было ли осуществлено хоть одно попадание с целями. Аргумент queryTriggerInteraction не обязателен

\---

\### ƒ OverlapSphereNonAlloc

\`\`\`lua

Physic.OverlapSphereNonAlloc(origin, radius, maxResults, layerMask, queryTriggerInteraction)

\`\`\`

\*\*Return:\*\* \`Transform\[\]\`

\*\*Description:\*\* Создает сферу, которая возвращает список ВСЕХ объектов на своем пути(ограничивается аргументом maxResults). Аргумент queryTriggerInteraction обязателен

\---

\### ƒ OverlapBox

\`\`\`lua

Physic.OverlapBox(center, halfExtents, rotation(Vector4), layerMask)

\`\`\`

\*\*Return:\*\* \`Transform\[\]\`

\*\*Description:\*\* Проверяет кубическую область на наличие коллайдеров. Полезно для взрывов или урона по площади

\---

\### ƒ OverlapBoxNonAlloc

\`\`\`lua

Physic.OverlapBoxNonAlloc(center, halfExtents, rotation(Vector4), maxResults, layerMask)

\`\`\`

\*\*Return:\*\* \`Transform\[\]\`

\*\*Description:\*\* Проверяет кубическую область на наличие коллайдеров. Полезно для взрывов или урона по площади. Ограничивается maxResults

\---

\### ƒ OverlapCapsule

\`\`\`lua

Physic.OverlapCapsule(pointA, pointB, radius, layerMask)

\`\`\`

\*\*Return:\*\* \`Transform\[\]\`

\*\*Description:\*\* Проверяет капсульную область на наличие коллайдеров.

\---

\### ƒ ClosestPointToCollider

\`\`\`lua

Physic.ClosestPointToCollider(point, Component(collider))

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Возвращает ближайшую точку соприкосновения с коллайдером относительно точки

\---

\### ƒ ComputePenetration

\`\`\`lua

Physic.ComputePenetration(aComp, aPos, aRot(Vector4), bComp, bPos, bRot(Vector4))

\`\`\`

\*\*Return:\*\* \`PenetrationInfo\`

\*\*Description:\*\* Считает коофиценты соприкосновения коллайдеров. Полезно для замены сложных математических операций

\---

\### ƒ DistanceBetweenColliders

\`\`\`lua

Physic.DistanceBetweenColliders(aComp, bComp)

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Возвращает расстояние между коллайдерами

\---

\### ƒ ClosestPoint

\`\`\`lua

Physic.ClosestPoint(point, transformTarget)

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Возвращает ближайшую точку к таргету

\---

\## 📦 Player

\### ƒ ShowSubtitles

\`\`\`lua

Player.ShowSubtitles(msg, color_r, color_g, color_b, importance, shake, reset)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Показывает субтитры указанному игроку с настройкой цвета и тряски.

\---

\### ƒ GetLocal

\`\`\`lua

Player.GetLocal()

\`\`\`

\*\*Return:\*\* \`Player\`

\*\*Description:\*\* Возвращает локального игрока (ВАС). Используйте для изменения своего здоровья, оружия и т.д.

\---

\### ƒ GetAllPlayers

\`\`\`lua

Player.GetAllPlayers()

\`\`\`

\*\*Return:\*\* \`Player\[\]\`

\*\*Description:\*\* Возвращает список всех игроков на сервере.

\---

\### ƒ GetName

\`\`\`lua

Player.GetName()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает видимый никнейм игрока.

\---

\### ƒ GetID

\`\`\`lua

Player.GetID()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает уникальный сетевой ID номер игрока.

\---

\### ƒ GetBadgeID

\`\`\`lua

Player.GetBadgeID()

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Возвращает числовой ID иконки рядом с ником (1=Разработчик, 2=Админ и т.д.).

\---

\### ƒ GetSpeaking

\`\`\`lua

Player.GetSpeaking()

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Возвращает true, если игрок сейчас использует голосовой чат.

\---

\### ƒ GetMuted

\`\`\`lua

Player.GetMuted()

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Возвращает true, если вы заглушили этого игрока у себя.

\---

\### ƒ IsHost

\`\`\`lua

Player.IsHost()

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Возвращает true, если этот игрок создал сервер (Имеет права хоста/админа).

\---

\### ƒ Kick

\`\`\`lua

Player.Kick()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Исключает игрока с сервера.

\---

\### ƒ Ban

\`\`\`lua

Player.Ban()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Банит игрока на сервере.

\---

\### ƒ GetCharacter

\`\`\`lua

Player.GetCharacter()

\`\`\`

\*\*Return:\*\* \`Transform\`

\*\*Description:\*\* Возвращает игровую модель игрока(требуется много NRE проверок)

\*\*Example:\*\*

\`\`\`lua

function ChangePlayerScale(scale)

local localPlayer = Player.GetLocal() if localPlayer == nil or not localPlayer.IsValid() then return end local localPlayerCharacter = localPlayer.GetCharacter() if localPlayerCharacter == nil or not localPlayerCharacter.IsValid() then return end localPlayerCharacter.LocalScale = scale
end

\`\`\`

\---

\### p IsCriminal

\`\`\`lua

Player.IsCriminal

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Является ли данный игрок преступником?

\---

\### p Criminality

\`\`\`lua

Player.Criminality

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Коэффициент преступности игрока. Варьируется от 0 до 100

\---

\### p CriminalityLevel

\`\`\`lua

Player.CriminalityLevel

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Кол-во звезд преступника у игрока

\---

\### p Team

\`\`\`lua

Player.Team

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Описывает текущую команду игрока. Пока-что работает только локально, если использовать переменную как геттер

\---

\### ƒ GiveCash

\`\`\`lua

Player.GiveCash(count)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Выдает деньги игроку

\---

\### ƒ RemoveCash

\`\`\`lua

Player.RemoveCash(count)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Забирает деньги у игрока

\---

\### ƒ Teleport

\`\`\`lua

Player.Teleport(position)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Телепортирует игрока в заданную позицию

\---

\### ƒ SendChatMessage

\`\`\`lua

Player.SendChatMessage(message)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Отправляет сообщение только ЭТОМУ игроку

\---

\## 📦 PlayerMaster

\### p Health

\`\`\`lua

PlayerMaster.Health

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Текущее количество здоровья игрока.

\---

\### p MaxHealth

\`\`\`lua

PlayerMaster.MaxHealth

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Максимальный лимит здоровья.

\---

\### p Speed

\`\`\`lua

PlayerMaster.Speed

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Множитель скорости передвижения (По умолч.: 1.0).

\---

\### p Endurance

\`\`\`lua

PlayerMaster.Endurance

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Множитель сопротивления урону. Меньшие значения означают меньше полученного урона.

\---

\### p Dexterity

\`\`\`lua

PlayerMaster.Dexterity

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Влияет на скорость обращения с оружием и время перезарядки.

\---

\### p Stamina

\`\`\`lua

PlayerMaster.Stamina

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Текущий уровень выносливости для бега.

\---

\### p Currency

\`\`\`lua

PlayerMaster.Currency

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Количество денег, которое сейчас есть у игрока.

\---

\### p Air

\`\`\`lua

PlayerMaster.Air

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Уровень кислорода (0-100) при нахождении под водой.

\---

\### p Blood

\`\`\`lua

PlayerMaster.Blood

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Количество крови (влияет на сознание/смерть).

\---

\### p Pain

\`\`\`lua

PlayerMaster.Pain

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Уровень боли. Сильная боль вызывает размытие экрана и спотыкание.

\---

\### p Poison

\`\`\`lua

PlayerMaster.Poison

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Уровень токсичности. Высокие значения постепенно отнимают здоровье.

\---

\### p Dizzyness

\`\`\`lua

PlayerMaster.Dizzyness

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Уровень головокружения. При высоких значениях камера шатается, и игрок падает.

\---

\### p Adrenaline

\`\`\`lua

PlayerMaster.Adrenaline

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Уровень адреналина. Временно увеличивает скорость и игнорирует боль.

\---

\### p Condition

\`\`\`lua

PlayerMaster.Condition

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Сердечный ритм (BPM). Экстремальные значения ведут к остановке сердца.

\---

\### p CurrentItem

\`\`\`lua

PlayerMaster.CurrentItem

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Индекс текущего экипированного предмета.

\---

\### p CurrentWeaponName

\`\`\`lua

PlayerMaster.CurrentWeaponName

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Название оружия, которое сейчас в руках.

\---

\### p SpawnablePath

\`\`\`lua

PlayerMaster.SpawnablePath

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Путь к ресурсу текущей модели персонажа.

\---

\### p Cripple

\`\`\`lua

PlayerMaster.Cripple

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Если true, ноги игрока сломаны, и он не может бегать.

\---

\### p Grounded

\`\`\`lua

PlayerMaster.Grounded

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* True, если игрок касается земли.

\---

\### p Invisible

\`\`\`lua

PlayerMaster.Invisible

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Делает бессмертным игрока

\---

\### p InfiniteStamina

\`\`\`lua

PlayerMaster.InfiniteStamina

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Игрок может бегать бесконечно, не уставая.

\---

\### p CreatorMode

\`\`\`lua

PlayerMaster.CreatorMode

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Включает творческий режим (полет, бессмертие и т.д.).

\---

\### p NoReloading

\`\`\`lua

PlayerMaster.NoReloading

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Оружие никогда не требует перезарядки.

\---

\### p InfiniteAmmo

\`\`\`lua

PlayerMaster.InfiniteAmmo

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Количество патронов никогда не уменьшается.

\---

\### p NoclipPerms

\`\`\`lua

PlayerMaster.NoclipPerms

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Флаг прав: Разрешает игроку использовать noclip (ходьба сквозь стены).

\---

\### p IgnoredByAI

\`\`\`lua

PlayerMaster.IgnoredByAI

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* ИИ будет полностью игнорировать игрока, даже если его атаковать.

\---

\### p HideUI

\`\`\`lua

PlayerMaster.HideUI

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Скрывает весь интерфейс (Здоровье, патроны, прицел). Хорошо для кино.

\---

\### p ActionCam

\`\`\`lua

PlayerMaster.ActionCam

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Включает режим динамической камеры, обычно для трюков на транспорте.

\---

\### p RenderHands

\`\`\`lua

PlayerMaster.RenderHands

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Переключает отображение рук игрока от первого лица.

\---

\### p RenderLegs

\`\`\`lua

PlayerMaster.RenderLegs

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Переключает отображение ног игрока, видимых при взгляде вниз.

\---

\### p InUI

\`\`\`lua

PlayerMaster.InUI

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* True, если у игрока сейчас открыто меню.

\---

\### p InBoss

\`\`\`lua

PlayerMaster.InBoss

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Активирует интерфейс битвы с боссом.

\---

\### p ToolgunMode

\`\`\`lua

PlayerMaster.ToolgunMode

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Числовой ID выбранного режима Тулгана.

\---

\### ƒ Damage

\`\`\`lua

PlayerMaster.Damage(damage, bldMultiper, limb)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Наносит урон игроку. Аргументы: Кол-во, Множ.Крови, ИмяКонечности.

\---

\### ƒ Heal

\`\`\`lua

PlayerMaster.Heal(amount, limb)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Лечит определенное количество здоровья конечности.

\---

\### ƒ HealFully

\`\`\`lua

PlayerMaster.HealFully()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Полностью восстанавливает здоровье, кровь и чинит все сломанные конечности.

\---

\### ƒ Kill

\`\`\`lua

PlayerMaster.Kill(ragdoll)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Мгновенно убивает игрока. Передайте 'true', чтобы включить физику рэгдолла.

\---

\### ƒ Ragdoll

\`\`\`lua

PlayerMaster.Ragdoll(active)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Заставляет игрока упасть в режим рэгдолла.

\---

\### ƒ GetUp

\`\`\`lua

PlayerMaster.GetUp()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Поднимает игрока из режима рэгдолла.

\---

\### ƒ Knockdown

\`\`\`lua

PlayerMaster.Knockdown(force, dir)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Сбивает игрока с ног с определенной физической силой и направлением.

\---

\### ƒ Emote

\`\`\`lua

PlayerMaster.Emote(name)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Проигрывает анимацию эмоции по имени (напр. 'Dance').

\---

\### ƒ EndEmote

\`\`\`lua

PlayerMaster.EndEmote()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Останавливает текущую эмоцию.

\---

\### ƒ GiveWeapon

\`\`\`lua

PlayerMaster.GiveWeapon(name, ammo, color, extraMag, skin, scope, barrel, shield)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Выдает игроку оружие с указанными модулями и настройками.

\---

\### ƒ RemoveWeapon

\`\`\`lua

PlayerMaster.RemoveWeapon(name)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Удаляет конкретное оружие по имени из инвентаря.

\---

\### ƒ ClearWeapons

\`\`\`lua

PlayerMaster.ClearWeapons()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Удаляет ВСЕ оружие из инвентаря.

\---

\### ƒ DropWeapon

\`\`\`lua

PlayerMaster.DropWeapon(index)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Выбрасывает оружие, находящееся под указанным индексом инвентаря.

\---

\### ƒ DropCurrency

\`\`\`lua

PlayerMaster.DropCurrency(amount)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Выбрасывает указанную сумму денег на землю.

\---

\### ƒ SetScale

\`\`\`lua

PlayerMaster.SetScale(scale)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Устанавливает множитель размера игрока (напр. 0.5 = Гном, 2.0 = Гигант).

\---

\### ƒ SetTeam

\`\`\`lua

PlayerMaster.SetTeam(team)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Назначает игрока в команду (напр. 'Red', 'Blue').

\---

\### ƒ GetHeldWeaponInfo

\`\`\`lua

PlayerMaster.GetHeldWeaponInfo()

\`\`\`

\*\*Return:\*\* \`WeaponInfo\`

\*\*Description:\*\* Возвращает объект с подробной информацией о текущем оружии в руках.

\---

\### ƒ GetLimbs

\`\`\`lua

PlayerMaster.GetLimbs()

\`\`\`

\*\*Return:\*\* \`string\[\]\`

\*\*Description:\*\* Возвращает список имен всех частей тела.

\---

\### ƒ IsValid

\`\`\`lua

PlayerMaster.IsValid()

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет, валиден и активен ли компонент PlayerMaster.

\---

\## 📦 RaycastInfo

\### p wasHit

\`\`\`lua

RaycastInfo.wasHit

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Попал ли рейкаст?

\---

\### p hit

\`\`\`lua

RaycastInfo.hit

\`\`\`

\*\*Return:\*\* \`Transform\`

\*\*Description:\*\* обьект, куда попал рейкаст(возможны NRE)

\---

\### p normal

\`\`\`lua

RaycastInfo.normal

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Нормаль попадания рейкаста

\---

\### p point

\`\`\`lua

RaycastInfo.point

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Точка попадания рейкаста

\---

\## 📦 Sprite

\### p New

\`\`\`lua

Sprite.New

\`\`\`

\*\*Return:\*\* \`Sprite\`

\*\*Description:\*\* Создает новый спрайт на основе переданной текстуры. Используется в UI.

\---

\### ƒ GetWidth

\`\`\`lua

Sprite.GetWidth()

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Возвращает ширину спрайта в пикселях.

\---

\### ƒ GetHeight

\`\`\`lua

Sprite.GetHeight()

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Возвращает высоту спрайта в пикселях.

\---

\### ƒ Texture

\`\`\`lua

Sprite.Texture()

\`\`\`

\*\*Return:\*\* \`Texture\`

\*\*Description:\*\* Возвращает текстуру, из которой сделан этот спрайт.

\---

\### ƒ IsValid

\`\`\`lua

Sprite.IsValid()

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет, существует ли спрайт (не был ли он удален).

\---

\## 📦 String

\### ƒ startsWith

\`\`\`lua

String.startsWith(prefix)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет, начинается ли строка с указанного префикса.

\---

\### ƒ endsWith

\`\`\`lua

String.endsWith(suffix)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет, заканчивается ли строка указанным суффиксом.

\---

\### ƒ contains

\`\`\`lua

String.contains(substring)

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет, содержит ли строка указанную подстроку.

\---

\## 📦 Texture

\### p texture

\`\`\`lua

Texture.texture

\`\`\`

\*\*Return:\*\* \`Texture2D\`

\*\*Description:\*\* Внутренняя ссылка на нативную Unity Texture2D.

\---

\### ƒ GetWidth

\`\`\`lua

Texture.GetWidth()

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Возвращает ширину изображения в пикселях.

\---

\### ƒ GetHeight

\`\`\`lua

Texture.GetHeight()

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Возвращает высоту изображения в пикселях.

\---

\### ƒ IsValid

\`\`\`lua

Texture.IsValid()

\`\`\`

\*\*Return:\*\* \`bool\`

\*\*Description:\*\* Проверяет, корректно ли загружена текстура в память.

\---

\### ƒ GetPixels

\`\`\`lua

Texture.GetPixels()

\`\`\`

\*\*Return:\*\* \`Vector4\[\]\`

\*\*Description:\*\* Возвращает массив цветов всех пикселей. Медленная операция!

\---

\### ƒ ToSprite

\`\`\`lua

Texture.ToSprite()

\`\`\`

\*\*Return:\*\* \`Sprite\`

\*\*Description:\*\* Конвертирует Texture2D в Sprite (нужно для компонентов UI Image).

\---

\### ƒ SetPixels

\`\`\`lua

Texture.SetPixels(pixels\[\])

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Задает пиксели текстуре с помощью из массива пикселей формата Vector4

\---

\## 📦 Time

\### p TimeScale

\`\`\`lua

Time.TimeScale

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Скорость течения времени. 1.0 — норма, 0.5 — замедление, 0 — пауза.

\---

\### p DeltaTime

\`\`\`lua

Time.DeltaTime

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Время в секундах, затраченное на последний кадр. Умножайте движение на это значение для плавности.

\---

\### p UnscaledDeltaTime

\`\`\`lua

Time.UnscaledDeltaTime

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Время кадра, игнорирующее TimeScale. Полезно для анимаций меню во время паузы.

\---

\### p GetRealTime

\`\`\`lua

Time.GetRealTime

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает текущее системное время компьютера (строка).

\---

\### p GetRealTimeMs

\`\`\`lua

Time.GetRealTimeMs

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Возвращает текущее системное время в миллисекундах (float).

\---

\## 📦 Transform

\### p Position

\`\`\`lua

Transform.Position

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Глобальная мировая позиция (Vector3).

\---

\### p LocalPosition

\`\`\`lua

Transform.LocalPosition

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Позиция относительно родительского объекта.

\---

\### p Rotation

\`\`\`lua

Transform.Rotation

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Глобальное вращение в углах Эйлера (Градусы X, Y, Z).

\---

\### p LocalRotation

\`\`\`lua

Transform.LocalRotation

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Вращение относительно родителя.

\---

\### p LocalScale

\`\`\`lua

Transform.LocalScale

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Размер относительно родителя. (1,1,1) — норма.

\---

\### p Forward

\`\`\`lua

Transform.Forward

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Синяя ось (Z+). Куда смотрит объект.

\---

\### p Right

\`\`\`lua

Transform.Right

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Красная ось (X+). Правая сторона объекта.

\---

\### p Up

\`\`\`lua

Transform.Up

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Зеленая ось (Y+). Верх объекта.

\---

\### p Parent

\`\`\`lua

Transform.Parent

\`\`\`

\*\*Return:\*\* \`Transform\`

\*\*Description:\*\* Родительский Transform. Nil означает корневой объект.

\---

\### p ChildCount

\`\`\`lua

Transform.ChildCount

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Количество дочерних объектов.

\---

\### p GameObject

\`\`\`lua

Transform.GameObject

\`\`\`

\*\*Return:\*\* \`GameObject\`

\*\*Description:\*\* GameObject, к которому прикреплен этот Transform.

\---

\### ƒ SetParent

\`\`\`lua

Transform.SetParent(parent, worldPositionStays)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Прикрепляет объект к родителю. Арг: Родитель, СохранитьПозицию.

\---

\### ƒ LookAt

\`\`\`lua

Transform.LookAt(target)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Поворачивает объект лицом к точке.

\---

\### ƒ GetChild

\`\`\`lua

Transform.GetChild(index)

\`\`\`

\*\*Return:\*\* \`Transform\`

\*\*Description:\*\* Получает ребенка по индексу (0 до Count-1).

\---

\### ƒ Find

\`\`\`lua

Transform.Find(name)

\`\`\`

\*\*Return:\*\* \`Transform\`

\*\*Description:\*\* Ищет глубокого ребенка по пути (напр., 'Arm/Hand').

\---

\### ƒ GetRoots

\`\`\`lua

Transform.GetRoots()

\`\`\`

\*\*Return:\*\* \`Transform\[\]\`

\*\*Description:\*\* Возвращает все корневые объекты сцены.

\---

\### ƒ DetachChildren

\`\`\`lua

Transform.DetachChildren()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Отсоединяет всех детей, делая их независимыми.

\---

\### ƒ GetSiblingIndex

\`\`\`lua

Transform.GetSiblingIndex()

\`\`\`

\*\*Return:\*\* \`int\`

\*\*Description:\*\* Получает порядковый номер среди 'братьев'.

\---

\### ƒ SetSiblingIndex

\`\`\`lua

Transform.SetSiblingIndex(index)

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Задает порядковый номер. Для сортировки UI.

\---

\### ƒ SetAsFirstSibling

\`\`\`lua

Transform.SetAsFirstSibling()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Перемещает в начало списка (Первый в UI).

\---

\### ƒ SetAsLastSibling

\`\`\`lua

Transform.SetAsLastSibling()

\`\`\`

\*\*Return:\*\* \`void\`

\*\*Description:\*\* Перемещает в конец списка (Последний в UI).

\---

\### ƒ GetPlayer

\`\`\`lua

Transform.GetPlayer(player)

\`\`\`

\*\*Return:\*\* \`Transform\`

\*\*Description:\*\* Конвертирует объект Player в Transform.

\---

\## 📦 Vector2

\### ƒ New

\`\`\`lua

Vector2.New(x, y)

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* Создает новый 2D вектор (X, Y). Обычно для интерфейса.

\---

\### p x

\`\`\`lua

Vector2.x

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Координата X.

\---

\### p y

\`\`\`lua

Vector2.y

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Координата Y.

\---

\### p Zero

\`\`\`lua

Vector2.Zero

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* (0, 0).

\---

\### p One

\`\`\`lua

Vector2.One

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* (1, 1).

\---

\### p Up

\`\`\`lua

Vector2.Up

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* (0, 1).

\---

\### p Down

\`\`\`lua

Vector2.Down

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* (0, -1).

\---

\### p Left

\`\`\`lua

Vector2.Left

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* (-1, 0).

\---

\### p Right

\`\`\`lua

Vector2.Right

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* (1, 0).

\---

\### ƒ Add

\`\`\`lua

Vector2.Add(other)

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* Складывает два вектора.

\---

\### ƒ Sub

\`\`\`lua

Vector2.Sub(other)

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* Вычитает векторы.

\---

\### ƒ Mul

\`\`\`lua

Vector2.Mul(scalar)

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* Умножает на число.

\---

\### ƒ Div

\`\`\`lua

Vector2.Div(scalar)

\`\`\`

\*\*Return:\*\* \`Vector2\`

\*\*Description:\*\* Делит на число.

\---

\### ƒ ToString

\`\`\`lua

Vector2.ToString()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает строковое представление.

\---

\## 📦 Vector3

\### ƒ New

\`\`\`lua

Vector3.New(x, y, z)

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Создает новый 3D вектор (X, Y, Z).

\---

\### p x

\`\`\`lua

Vector3.x

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Координата X (Вправо/Влево).

\---

\### p y

\`\`\`lua

Vector3.y

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Координата Y (Вверх/Вниз).

\---

\### p z

\`\`\`lua

Vector3.z

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Координата Z (Вперед/Назад).

\---

\### p Zero

\`\`\`lua

Vector3.Zero

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Сокращение для (0, 0, 0).

\---

\### p One

\`\`\`lua

Vector3.One

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Сокращение для (1, 1, 1).

\---

\### p Up

\`\`\`lua

Vector3.Up

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Сокращение для (0, 1, 0).

\---

\### p Down

\`\`\`lua

Vector3.Down

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Сокращение для (0, -1, 0).

\---

\### ƒ Add

\`\`\`lua

Vector3.Add(other)

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Складывает два вектора (a + b).

\---

\### ƒ Sub

\`\`\`lua

Vector3.Sub(other)

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Вычитает вектор b из a.

\---

\### ƒ Mul

\`\`\`lua

Vector3.Mul(scalar)

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Умножает вектор на число (Масштабирование).

\---

\### ƒ Div

\`\`\`lua

Vector3.Div(scalar)

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Делит вектор на число.

\---

\### ƒ ToVector3

\`\`\`lua

Vector3.ToVector3()

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Преобразует объект (например, Lua таблицу) в Vector3.

\---

\### ƒ ToString

\`\`\`lua

Vector3.ToString()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает читаемую строку вида '(x, y, z)'.

\---

\### ƒ ToQuanterion

\`\`\`lua

Vector3.ToQuanterion(other)

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Преобразует вектор (углы Эйлера) в кватернион вращения.

\---

\## 📦 Vector4

\### ƒ New

\`\`\`lua

Vector4.New(x, y, z, w)

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Создает 4D вектор или Цвет (R, G, B, A).

\---

\### p x

\`\`\`lua

Vector4.x

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* X или Красный канал.

\---

\### p y

\`\`\`lua

Vector4.y

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Y или Зеленый канал.

\---

\### p z

\`\`\`lua

Vector4.z

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* Z или Синий канал.

\---

\### p w

\`\`\`lua

Vector4.w

\`\`\`

\*\*Return:\*\* \`float\`

\*\*Description:\*\* W или Альфа (Прозрачность).

\---

\### p Zero

\`\`\`lua

Vector4.Zero

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* (0, 0, 0, 0). Прозрачный черный.

\---

\### p One

\`\`\`lua

Vector4.One

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* (1, 1, 1, 1). Непрозрачный белый.

\---

\### ƒ Add

\`\`\`lua

Vector4.Add(other)

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Складывает вектора.

\---

\### ƒ Sub

\`\`\`lua

Vector4.Sub(other)

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Вычитает вектора.

\---

\### ƒ Mul

\`\`\`lua

Vector4.Mul(scalar)

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Умножает (Делает цвет ярче).

\---

\### ƒ Div

\`\`\`lua

Vector4.Div(scalar)

\`\`\`

\*\*Return:\*\* \`Vector4\`

\*\*Description:\*\* Делит (Затемняет цвет).

\---

\### ƒ ToEuler

\`\`\`lua

Vector4.ToEuler()

\`\`\`

\*\*Return:\*\* \`Vector3\`

\*\*Description:\*\* Преобразует Кватернион (Вращение) в углы Эйлера (Vector3).

\---

\### ƒ ToString

\`\`\`lua

Vector4.ToString()

\`\`\`

\*\*Return:\*\* \`string\`

\*\*Description:\*\* Возвращает строковое представление.

\---
