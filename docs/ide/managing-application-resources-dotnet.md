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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e53c3701e31733c54869c71820956d674ed4fb8b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593700"
---
# <a name="manage-application-resources-net"></a>Uygulama kaynaklarını yönetme (.NET)

Kaynak dosyaları, uygulamanın bir parçası olan ancak simge dosyaları veya ses dosyaları gibi derlenmemiş dosyalardır. Bu dosyalar derleme işleminin bir parçası olmadığından, ikili dosyalarınızı yeniden derlemek zorunda kalmadan bunları değiştirebilirsiniz. Uygulamanızı yerelleştirmeyi planlıyorsanız, uygulamanızı yerelleştirdiğinizde değiştirilmesi gereken tüm dizeleri ve diğer kaynaklar için kaynak dosyalarını kullanmanız gerekir.

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio için uygulama [kaynaklarını yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-app-resources)adresine bakın.

.NET masaüstü uygulamalarındaki kaynaklar hakkında daha fazla bilgi için [masaüstü uygulamalarındaki Kaynaklar'a](/dotnet/framework/resources/index)bakın.

## <a name="work-with-resources"></a>Kaynaklarla çalışma

Yönetilen kod projesinde, proje özellikleri penceresini açın. Özellikler penceresini aşağıdakilerden biri ile açabilirsiniz:

- **Çözüm Gezgini'nde** proje düğümüne sağ tıklayıp **Özellikleri** seçme
- **Ctrl**+**Q** arama kutusuna **proje özelliklerini** yazma
- **Çözüm Gezgininde** **Alt**+**Girin'i** Seçme

**Kaynaklar** sekmesini seçin. Projenizde zaten bir dosya yoksa bir *.resx* dosyası ekleyebilirsiniz, farklı türde kaynak ekleyebilir ve silebilirsiniz ve varolan kaynakları değiştirebilirsiniz.

## <a name="resources-in-other-project-types"></a>Diğer proje türlerindeki kaynaklar

Kaynaklar .NET projelerinde diğer proje türlerine göre farklı yönetilir. Kaynaklar hakkında daha fazla bilgi için:

- Evrensel Windows Platformu (UWP) uygulamaları, Bkz. [Uygulama kaynakları ve Kaynak Yönetim Sistemi](/windows/uwp/app-resources/)
- C++ projeleri, bkz. [kaynak dosyalarıyla çalışma](/cpp/windows/working-with-resource-files) ve [nasıl kullanılır: Kaynak oluşturma](/cpp/windows/how-to-create-a-resource)

## <a name="see-also"></a>Ayrıca bkz.

- [Masaüstü uygulamalarındaki kaynaklar (.NET Framework)](/dotnet/framework/resources/index)
- [Uygulama kaynaklarını yönetme (Mac için Visual Studio)](/visualstudio/mac/managing-app-resources)
