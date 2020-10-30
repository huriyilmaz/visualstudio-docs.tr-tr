---
title: .NET Framework uzantıları kaydediliyor | Microsoft Docs
description: .NET Framework belirli bir sürümünü sistem kayıt defterine genişleten bir derlemeyi içeren bir klasör eklemeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: d63dda9cab50474fd357043d5f694a645a18b2b9
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048751"
---
# <a name="register-extensions-of-the-net-framework"></a>.NET Framework uzantılarını Kaydet

.NET Framework belirli bir sürümünü genişleten bir derleme geliştirebilirsiniz. Derlemenin Visual Studio **başvuruları Ekle** iletişim kutusunda görünmesini etkinleştirmek için, onu içeren klasörü sistem kayıt defterine eklemeniz gerekir.

 Örneğin, Trey Research şirketinin .NET Framework 4 ' ü genişleten bir kitaplık geliştirdiğini ve bir proje .NET Framework 4 ' ü hedeflediğinde **Başvuru Ekle** iletişim kutusunda kitaplık derlemelerinin görünmesini istediğini varsayalım. Ayrıca, derlemelerin 32 bit bilgisayarda çalışan 32 bitlik derlemeler veya bir 64 bit bilgisayarda çalışan 64 bit derlemeler olduğunu ve *C:\TreyResearch\Extensions4 \\* klasörüne yükleneceğini varsayın.

 Bu klasörü şu anahtarı kullanarak kaydedin: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\ . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch \\** . Anahtara şu varsayılan değeri verin: **C:\TreyResearch\Extensions4** .

> [!NOTE]
> .NET Framework sürümünün derleme numarası farklı olabilir.

 32 bitlik bir derlemeyi 64 bit bilgisayara kaydetmek için Wow6432 düğümünü kullanın, örneğin: **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\ . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch \\** .

### <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio tümleştirmesi](../msbuild/visual-studio-integration-msbuild.md)
