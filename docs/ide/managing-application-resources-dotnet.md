---
title: Uygulama kaynaklarını yönetme (.NET)
description: Derleme işleminin parçası olan uygulama kaynakları dosyalarını yönetmeyi öğrenin.
ms.custom: SEO-VS-2020
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
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 4698bcf3ba1833cec700f3e1446c105aa3c9a0fa
ms.sourcegitcommit: 965372ad0d75f015403c1af508080bf799914ce3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/12/2022
ms.locfileid: "135805812"
---
# <a name="manage-application-resources-net"></a>Uygulama kaynaklarını yönetme (.NET)

Kaynak dosyaları, bir uygulamanın parçası olan ancak simge dosyaları veya ses dosyaları gibi derlenmiş dosyalardır. Bu dosyalar derleme işleminin parçası değildir, ikili dosyalarınızı yeniden derlemek zorunda kalmadan bunları değiştirebilirsiniz. Uygulamanızı yerelleştirmeyi planlıyorsanız, kaynak dosyalarını, uygulama yerelleştirmeniz gerekirken değişmesi gereken tüm dizeler ve diğer kaynaklar için kullansanız gerekir.

> [!NOTE]
> Bu konu, Visual Studio için Windows. Daha Mac için Visual Studio için [bkz. Uygulama kaynaklarını yönetme (Mac için Visual Studio).](/visualstudio/mac/managing-app-resources)

.NET uygulamaları kaynakları hakkında daha fazla bilgi için [bkz. .NET uygulamaları kaynakları.](/dotnet/framework/resources/index)

## <a name="work-with-resources"></a>Kaynaklarla çalışma

Yönetilen kod projesinde proje özellikleri penceresini açın. Özellikler penceresini şu iki şekilde açabilirsiniz:

- Kümede proje düğümüne sağ **Çözüm Gezgini** ve Özellikler'i **seçme**
- **Ctrl** Q **arama** kutusuna + **proje** özelliklerini yazma
- Çözüm Gezgini'de **Alt** + **Enter** **tuşuna Çözüm Gezgini**

Kaynaklar **sekmesini** seçin. Projeniz zaten bir tane içeriyorsa *bir .resx* dosyası ekleyebilir, farklı türlerde kaynaklar ekleyebilir ve silebilir ve mevcut kaynakları değiştirebilirsiniz.

## <a name="resources-in-other-project-types"></a>Diğer proje türlerinde kaynaklar

Kaynaklar, .NET projelerinde diğer proje türlerinden farklı yönetilir. Kaynaklar hakkında daha fazla bilgi için:

- Evrensel Windows Platformu (UWP) uygulamaları, [bkz. Uygulama kaynakları ve Kaynak Yönetimi Sistemi](/windows/uwp/app-resources/)
- C++ projeleri, [bkz. Kaynak dosyalarıyla çalışma](/cpp/windows/working-with-resource-files) [ve Nasıl kullanılır: Kaynak oluşturma](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET uygulamaları (.NET Framework)](/dotnet/framework/resources/index)
- [Uygulama kaynaklarını yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-app-resources)
