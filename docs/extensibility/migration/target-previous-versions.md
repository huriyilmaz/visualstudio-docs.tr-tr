---
title: Visual Studio 2022 RC 'de uzantı oluştururken hedef Visual Studio 2019
description: projeyi Visual Studio 2022 RC ile oluşturursanız Visual Studio uzantınızın Visual Studio 2019 ile nasıl çalıştığını öğrenin.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
monikerRange: vs-2022
ms.workload:
- vssdk
feedback_system: GitHub
ms.openlocfilehash: efd91e319b5b38d03bf58bd4e10a35cf9c7d8899
ms.sourcegitcommit: 72f8ce4992cc62c4833e6dcb0f79febb328c44be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/14/2021
ms.locfileid: "130011555"
---
# <a name="target-a-previous-version-when-creating-an-extension-in-visual-studio-2022-rc"></a>Visual Studio 2022 RC 'de uzantı oluştururken önceki bir sürümü hedefleyin

[!INCLUDE [preview-note](../includes/preview-note.md)]

Visual Studio 2022 RC kullanarak yeni bir vsıx projesi oluşturduğunuzda, proje, Visual Studio 2022 ' i hedefleyen bir şablondan oluşturulur. Visual Studio 2019 veya önceki bir sürümü hedeflemek istiyorsanız, oluşturulan projeyi değiştirmeniz gerekir.

uzantınızın çoğunu veya tamamını paylaşırken Visual Studio 2019 ve Visual Studio 2022 ' i hedeflemek için [paylaşılan projeler](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting) kullanmayı göz önünde bulundurun.

Visual Studio 2019 ' i hedefleyecek vsıx projesinde şu adımları uygulayın:

1. `source.extension.vsixmanifest` `ProductArchitecture` Öğeyi ve sürüm aralığını kaldırmak için dosyayı düzenleyin:

    ```diff
    -<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
    +<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[16.0,17.0)">
    -  <ProductArchitecture>amd64</ProductArchitecture>
     </InstallationTarget>
    ```

   Ayrıca önkoşulları güncelleştirin:

    ```diff
    -<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,18.0)" DisplayName="Visual Studio core editor" />
    +<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[16.0,17.0)" DisplayName="Visual Studio core editor" />
    ```

    Gerekli olabilecek diğer güncelleştirmeler için dosyayı gözden geçirin.

1. Proje dosyanızda başvurduğunuz VS SDK paketlerinin sürümlerini değiştirin:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    ```
