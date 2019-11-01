---
title: .NET Framework Hedefleme hatalarını giderme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.FrameworkTargetingErrors
- MSBuild.ResolveAssemblyReference.FailedToResolveReferenceBecausePrimaryAssemblyInExclusionList
helpviewer_keywords:
- targeting .NET Framework version [Visual Studio]
- versions [Visual Studio], .NET Framework Client Profile
- multi-targeting
- multitargeting
- .NET Framework Client Profile
ms.assetid: 830e3e45-9a93-4279-a249-75b84599aefb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 36401e2ac002a74cdab6e9c19373354f4eb6fb1e
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189428"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>.NET Framework Hedefleme hatalarını giderme
Bu konuda, başvuru sorunları ve bu hataları nasıl giderebileceğinizi belirten MSBuild hataları açıklanmaktadır.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>.NET Framework farklı bir sürümünü hedefleyen bir proje veya derlemeye başvurmuş olabilirsiniz
 .NET Framework farklı sürümlerini hedefleyen projelere veya derlemelere başvuran uygulamalar oluşturabilirsiniz. Örneğin, .NET Framework 4 için istemci profilini hedefleyen bir uygulama oluşturabilir, ancak .NET Framework 2,0 ' i hedefleyen bir derlemeye başvuru yapabilirsiniz. Ancak, .NET Framework önceki bir sürümünü hedefleyen bir proje oluşturursanız, bu projedeki bir başvuruyu, .NET Framework 4 veya .NET Framework 4 ' e ait istemci profilini hedefleyen bir proje veya derlemeye ayarlayamazsınız. Hatayı gidermek için uygulamanızın, uygulamanızın başvurduğu projeler veya derlemeler tarafından hedeflenen profille uyumlu bir profili veya profilleri hedeflediğinden emin olun.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Bir projeyi .NET Framework farklı bir sürümüne yeniden hedeflediniz
 Uygulamanız için .NET Framework hedef sürümünü değiştirirseniz, Visual Studio bazı başvuruları değiştirir ancak bazı başvuruları el ile güncelleştirmeniz gerekebilir. Örneğin, bir uygulamayı [!INCLUDE[net_v35SP1_long](../msbuild/includes/net_v35sp1_long_md.md)] hedefleyecek şekilde değiştirirseniz ve bu uygulamanın .NET Framework 4 ' e ait istemci profilini kullanan kaynakları veya ayarları varsa, daha önce bahsedilen hatalardan biri oluşabilir.

 Uygulama ayarlarını geçici olarak çözmek için **Çözüm Gezgini**açın, **tüm dosyaları göster**' i seçin ve ardından Visual Studio 'nun XML düzenleyicisinde *app. config* dosyasını düzenleyin. Ayarlarınızdaki sürümü .NET Framework uygun sürümüyle eşleşecek şekilde değiştirin. Örneğin, 4.0.0.0 olan sürüm ayarını 2.0.0.0 olarak değiştirebilirsiniz. Benzer şekilde, kaynakları ekleyen bir uygulama için **Çözüm Gezgini**açın, **tüm dosyaları göster** düğmesini seçin, **projem** (Visual Basic) veya **Properties** (C#) öğesini genişletin ve ardından *Resources. resx* dosyasını düzenleyin. Visual Studio 'nun XML düzenleyicisinde dosyası. 4\.0.0.0 olan sürüm ayarını 2.0.0.0 olarak değiştirin.

 Uygulamanızın simgeler veya bit eşlemler veya veri bağlantı dizeleri gibi ayarlar gibi kaynakları varsa, **Proje Tasarımcısı** 'nın **Ayarlar** sayfasındaki tüm öğeleri kaldırarak ve ardından gerekli ayarları yeniden ekleyerek hatayı çözebilirsiniz.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Bir projeyi .NET Framework farklı bir sürümüne yeniden hedeflediniz ve başvurular çözümlenmiyor
 Bir projeyi .NET Framework farklı bir sürümüne yeniden hedeflemeniz durumunda, başvurularınız bazı durumlarda düzgün şekilde çözümlenmeyebilir. Derlemelere yönelik açık tam başvurular genellikle bu soruna neden olur, ancak çözümlenmez olan başvuruları kaldırarak ve ardından projeye geri ekleyerek çözümü çözebilirsiniz. Alternatif olarak, başvuruları değiştirmek için proje dosyasını düzenleyebilirsiniz. İlk olarak, aşağıdaki formun başvurularını kaldırırsınız:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Daha sonra bunları basit formla değiştirirsiniz:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> Projenizi kapatıp yeniden açtıktan sonra tüm başvuruların doğru şekilde çözümlendiğinden emin olmak için yeniden oluşturmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: .NET Framework bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md)
- [.NET Framework istemci profili](/dotnet/framework/deployment/client-profile)
- [Çerçeve hedefleme genel bakış](../ide/visual-studio-multi-targeting-overview.md)
- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)