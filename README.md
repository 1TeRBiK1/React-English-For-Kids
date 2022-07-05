# Structure Project

```
- /src
    -  /Components - компоненты которые переиспользуются в разных страничках, не имеющие side effects(без обращения в DOM, Redux, GQL), сборище UI компонент+своих тэгов. Вложенная структура.
        *  /SomeName
            *   index.ts - default export
            *   index.module.scss - module scss
            *   SomeName.tsx - Presentions Components
            *   /NextSomeComponent - вложенный подкомпонент
    -   /Feature - компоненты переиспользуемые с логикой и side effects.
        *   /SomeName
            *   index.ts - default export
            *   index.module.scss - module scss
            *   SomeName.tsx - Component
            *   /NextSomeComponent - вложенный подкомпонент
    -   /Constants - глобальные константы. Например для билдов в прод или дев. Плоская структура.
        *   someConstants.ts
    -   /GlobalFunctions - обычные ts func, которые переиспользуются или имеют логику не связанную с компонентом(например исправление структуры с бэка во фронт, редактирование строки, работа с локалстораджем для запоминания локальных изменений). Плоская структура.
        *   someGlobalFunc.ts
    -   /Hooks - кастомные хуки. Плоская структура.
        *   useSomeName.ts
    -   /images - deprecated
    -   /Pages - страницы с разными урлами и главным файлом Routers.tsx для роутинга+авторизационной проверки. Вложенная структура.
        *   /SomeNamePage
            *   index.ts - default export
            *   index.module.scss - module scss
            *   SomeName.tsx - Компонент
            *   interfaces.ts - когда много интерфейсов в компоненте
            *   SomeName.query/mutation.graphql - in future (тут будем описывать стрингу gql запросов)
            *   SomeName.test.tsx - in future (тест на компонент)
            *   /NextSomeComponent

    -   /Store - Redux Store. Вложенная структура.
        *   combineRedusers.ts - сборка всех редьюсеров в проекте
        *   hooks.ts - кастомные хуки для типизации
        *   store.ts - global store redux
        *   /SomeName
            *   actions.ts - action func
            *   reduser.ts - redux reduser
            *   types.ts - all types of this reduser
            *   /SomeName
            *   if(вложенна еще) combineRedusers.ts
    -   /UI - typical inputs/buttons/forms/loaders. Вложенная структура
        *   Button.ts
        *   Input.ts
        *   if(SomeName > 1) => folder /SomeName
    -   /Common - папка для стандартных(тупых) вещей. Вложенная структура
        *   /images
        *   /fonts
```

# Rules order imports in Components

- React

- GQL

- Redux

- Interfaces

- Hooks

- Components/Features

- Simple func

- Constants

- scss files

Example:

```
import React, { useRef, useEffect, useState } from "react";

import { gql, useQuery } from "@apollo/client";

import { addBlur, durationTime } from "../../Store/Video/actions";

import { Video_Query } from "./interfaces";

import { useAppDispatch, useAppSelector } from "../../Store/hooks";
import useCreateRectangle from "../../Hooks/useCreateRectangle";

import NavigationInnacurate from "../../Components/NavigationInnacurate";
import NavigationAccurate from "../../Components/NavigationAccurate";
import Ruler from "../../Components/Ruler";
import ButtonsBlock from "../../Components/ButtonsBlock";
import SceneScroller from "../../Components/SceneScroller";
import ModalButton from "../../Components/ModalButton";
import ChapterSelector from "../../Components/ChapterSelector";
import ChapterScroller from "../../Components/ChapterScroller";
import NavigationBlur from "../../Components/NavigationBlur";
import CuttingVideoContainer from "../../Components/CuttingVideoContainer";

import styles from "./index.module.scss";

```
