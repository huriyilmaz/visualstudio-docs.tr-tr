---
title: Visual Studio 2022'de uzantı oluştururken 2019'Visual Studio hedefle
description: Visual Studio 2022 ile projeyi Visual Studio 2019 ile Visual Studio öğrenin.
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
ms.openlocfilehash: 22392f15590def9d068757ff54cb8667f54168c7
ms.sourcegitcommit: 932cf0f653c6258b73f42102d134cbaf50b8f20c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2021
ms.locfileid: "132880065"
---
# <a name="target-a-previous-version-when-creating-an-extension-in-visual-studio-2022"></a>Visual Studio 2022'de uzantı oluştururken önceki bir sürümü hedefleme

Visual Studio 2022 kullanarak yeni bir VSIX projesi oluşturulduğunda, proje 2022'ye yönelik bir şablondan Visual Studio oluşturulur. Visual Studio 2019 veya önceki bir sürümü hedeflemek için oluşturulan projeyi değiştirmeniz gerekir.

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
