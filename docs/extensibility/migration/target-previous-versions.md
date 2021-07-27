---
title: Visual Studio 2022 Preview'da uzantı oluştururken hedef Visual Studio 2019
description: Visual Studio 2022 Preview ile projeyi Visual Studio 2019 ile Visual Studio öğrenin.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
feedback_system: GitHub
ms.openlocfilehash: b6d8c21b2bb67664ceba348ef1ea9746305e3e8d
ms.sourcegitcommit: 3c5b1a1d51b521356f42a6879c1f1745573dda65
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2021
ms.locfileid: "114592235"
---
# <a name="target-a-previous-version-when-creating-an-extension-in-visual-studio-2022-preview"></a>Visual Studio 2022 Preview'da uzantı oluştururken önceki bir sürümü hedefleme

[!INCLUDE [preview-note](../includes/preview-note.md)]

Visual Studio 2022 Preview kullanarak yeni bir VSIX projesi oluşturulduğunda, proje 2022'yi Visual Studio oluşturulur. 2019 veya önceki Visual Studio bir sürümü hedeflemek için oluşturulan projeyi değiştirmeniz gerekir.

Uzantınıza [kodun çoğunu](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting) veya tüm Visual Studio 2019 ve Visual Studio 2022 hedeflerini hedeflemek için paylaşılan projeleri kullanmayı göz önünde bulundurabilirsiniz.

2019'da hedeflen vsIX Visual Studio izleyin:

1. öğesini `source.extension.vsixmanifest` ve sürüm aralığını `ProductArchitecture` kaldırmak için dosyasını düzenleyin:

    ```diff
    -<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
    +<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[16.0,17.0)">
    -  <ProductArchitecture>amd64</ProductArchitecture>
     </InstallationTarget>
    ```

   Ayrıca önkoşulları da güncelleştirin:

    ```diff
    -<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,18.0)" DisplayName="Visual Studio core editor" />
    +<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[16.0,17.0)" DisplayName="Visual Studio core editor" />
    ```

    Gerekli diğer güncelleştirmeler için dosyayı gözden geçirme.

1. Proje dosyanıza başvurarak VS SDK paketlerinin sürümlerini değiştirme:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    ```
