---
title: .NET Çerçevesi uzantılarının kaydedilmesi | Microsoft Dokümanlar
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
ms.openlocfilehash: e7f79e04cc9afb4238c9f6292a99da684066a7d5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632868"
---
# <a name="register-extensions-of-the-net-framework"></a>.NET Çerçevesi'nin uzantılarını kaydedin

.NET Framework'ün belirli bir sürümünü genişleten bir derleme geliştirebilirsiniz. Derlemenin Visual Studio **Add References** iletişim kutusunda görünmesini sağlamak için, bu klasörü içeren klasörü sistem kayıt defterine eklemeniz gerekir.

 Örneğin, Trey Research şirketinin .NET Framework 4'ü genişleten bir kitaplık geliştirdiğini ve bir proje .NET Framework 4'ü hedefaldığında **Kitaplık** derlemelerinin Add References iletişim kutusunda görünmesini istediğini varsayalım. Ayrıca, derlemelerin 64 bit bilgisayarda çalışan 32 bit bilgisayarda çalışan 32 bit veya 64 bit derlemeler olduğunu ve *bunların C:\TreyResearch\Extensions4\\ * klasörüne yükleneceğini varsayalım.

 Bu anahtarı kullanarak bu klasörü kaydolun: **\\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**. Anahtara bu varsayılan değeri verin: **C:\TreyResearch\Extensions4**.

> [!NOTE]
> .NET Framework sürümünün yapı numarası farklı olabilir.

 64 bit bilgisayarda 32 bit derleme kaydetmek için, örneğin: **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch\\**.

### <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ile tümleştirme](../msbuild/visual-studio-integration-msbuild.md)
