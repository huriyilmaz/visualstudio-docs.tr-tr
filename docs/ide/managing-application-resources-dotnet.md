---
title: Uygulama kaynaklarını yönetme (.NET)
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- msvse_resedit.dlg.SetCustomTool
- msvse_settingsdesigner.err.formatvalue
- msvse_resedit.err.nameblank
- msvse_resedit.err.duplicatename
helpviewer_keywords:
- Resource Designer
- resources [Visual Studio]
- Resources page in Project Designer
- application resources [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 29e4fbbd8d50001807f3d90a82d18e40a3674d01
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654256"
---
# <a name="manage-application-resources-net"></a>Uygulama kaynaklarını yönetme (.NET)

Kaynak dosyaları, bir uygulamanın parçası olan ancak derlenmediği, örneğin simge dosyaları veya ses dosyaları gibi dosyalardır. Bu dosyalar derleme sürecinin bir parçası olmadığından, ikili dosyalarınızı yeniden derlemek zorunda kalmadan bunları değiştirebilirsiniz. Uygulamanızı yerelleştirmek istiyorsanız, uygulamanızı yerelleştirmeniz durumunda değiştirilmesi gereken tüm dizelerin ve diğer kaynakların kaynak dosyalarını kullanmanız gerekir.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [uygulama kaynaklarını yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-app-resources).

.NET masaüstü uygulamalarındaki kaynaklar hakkında daha fazla bilgi için bkz. [masaüstü uygulamalarında kaynaklar](/dotnet/framework/resources/index).

## <a name="work-with-resources"></a>Kaynaklarla çalışma

Yönetilen bir kod projesinde proje özellikleri penceresini açın. Özellikler penceresini şu şekilde açabilirsiniz:

- **Çözüm Gezgini** ' de proje düğümüne sağ tıklayıp **Özellikler** ' i seçin
- **Ctrl** +**Q** arama kutusuna **Proje özellikleri** yazma
- **Alt** + Çözüm Gezgini**giriş** seçme

**Kaynaklar** sekmesini seçin. Projenizde bir tane yoksa bir *. resx* dosyası ekleyebilirsiniz, farklı türlerde kaynaklar ekleyip silebilir ve mevcut kaynakları değiştirebilirsiniz.

## <a name="resources-in-other-project-types"></a>Diğer proje türlerindeki kaynaklar

Kaynaklar, .NET projelerinde diğer proje türlerinden farklı şekilde yönetilir. İçindeki kaynaklar hakkında daha fazla bilgi için:

- Evrensel Windows Platformu (UWP) uygulamaları, bkz. [uygulama kaynakları ve kaynak yönetimi sistemi](/windows/uwp/app-resources/)
- C++projeler, bkz. [çalışma kaynak dosyaları](/cpp/windows/working-with-resource-files) ve [nasıl yapılır: kaynak oluşturma](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Ayrıca bkz.

- [Masaüstü uygulamalarındaki kaynaklar (.NET Framework)](/dotnet/framework/resources/index)
- [Uygulama kaynaklarını yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-app-resources)
