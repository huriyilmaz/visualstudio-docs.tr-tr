---
title: .NET Framework uzantıları kaydediliyor | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- Add References dialog box, registering extensions of the .NET Framework
- MSBuild, registering extensions of the .NET Framework
- .NET Framework extensions, registering
ms.assetid: deee6f53-ea87-4b88-a120-bea589822e03
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a5963faa5acb72ab0c94ca6b346456d83276e361
ms.sourcegitcommit: fb8babf5cd72f1fc2f97ffe4ad7b62d91f325f61
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2020
ms.locfileid: "64831494"
---
# <a name="registering-extensions-of-the-net-framework"></a>.NET Framework Uzantılarını Kaydetme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

.NET Framework belirli bir sürümünü genişleten bir derleme geliştirebilirsiniz. Derlemenin Visual Studio **başvuruları Ekle** iletişim kutusunda görünmesini etkinleştirmek için, onu içeren klasörü sistem kayıt defterine eklemeniz gerekir.  
  
 Örneğin, Trey Research şirketinin .NET Framework 4 ' ü genişleten bir kitaplık geliştirdiğini ve bir proje .NET Framework 4 ' ü hedeflediğinde **Başvuru Ekle** iletişim kutusunda kitaplık derlemelerinin görünmesini istediğini varsayalım. Ayrıca, derlemelerin 32 bit bilgisayarda çalışan 32 bitlik derlemeler veya bir 64 bit bilgisayarda çalışan 64 bit derlemeler olduğunu ve C:\TreyResearch\Extensions4\ klasörüne yükleneceğini varsayın.  
  
 Bu klasörü şu anahtarı kullanarak kaydedin: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft \\ . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch \\ . Anahtara şu varsayılan değeri verin: C:\TreyResearch\Extensions4.  
  
> [!NOTE]
> .NET Framework sürümünün derleme numarası farklı olabilir.  
  
 32 bitlik bir derlemeyi 64 bit bilgisayara kaydetmek için Wow6432 düğümünü kullanın, örneğin: HKEY_LOCAL_MACHINE \SOFTWARE\Wow6432Node\Microsoft \\ . NETFramework\v4.0.21006\AssemblyFoldersEx\TreyResearch \\ .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Studio tümleştirmesi](../msbuild/visual-studio-integration-msbuild.md)
