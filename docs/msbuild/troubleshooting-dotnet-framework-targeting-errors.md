---
title: .NET Framework Hedefleme Hatalarını Giderme | Microsoft Docs
description: Başvuru sorun MSBuild ortaya çıkabilir ve bu hataları nasıl çözy olabileceğiniz hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- dotnet
ms.openlocfilehash: a4f5af72bbc0a377b7876b858b58cffdaedff3391fda17f8df92a33cb94f7042
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121369728"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>.NET Framework hedefleme hatalarıyla ilgili sorunları giderme

Bu konu başlığında MSBuild sorunlardan kaynaklanabiliyor ve bu hataları nasıl çözebilirsiniz?

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>Projenin farklı bir sürümünü hedef alan bir projeye veya derlemeye başvur .NET Framework

 Uygulamanın farklı sürümlerini hedef alan projelere veya derlemelere başvurulan uygulamalar .NET Framework. Örneğin, .NET Framework 4 için istemci profilini hedef alan ancak .NET Framework 2.0'a yönelik bir derlemeye başvurabilirsiniz. Ancak, .NET Framework'ın önceki bir sürümünü hedef alan bir proje oluşturmanız, .NET Framework 4 veya .NET Framework 4'un kendisi için istemci profilini hedef alan bir proje veya derleme için bu projede bir başvuru ayarlayamzabilirsiniz. Hatayı çözmek için, uygulamanıza başvurulan projeler veya derlemeler tarafından hedeflenen profille uyumlu bir profili veya profilleri hedefleyenin.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Projeyi, projenin farklı bir sürümüne yeniden .NET Framework

 Uygulamanıza yönelik .NET Framework sürümünü değiştirir Visual Studio bazı başvuruları değiştirebilirsiniz, ancak bazı başvuruları el ile güncelleştirmeniz gerekebilir. Örneğin, bir uygulamayı .NET Framework 3.5 Service Pack 1'i hedef olarak değiştirir ve bu uygulamada .NET Framework 4 için istemci profiline bağlı kaynaklar veya ayarlar varsa, daha önce belirtilen hatalardan biri oluşabilir.

 Uygulama ayarlarıyla ilgili bir çalışma yapmak  **için Çözüm Gezgini** dosyasını açın, Tüm Dosyaları Göster'i seçin ve *app.config* xml düzenleyicisinde Visual Studio. Ayarlarda sürümü, uygulamanın uygun sürümüyle eş .NET Framework. Örneğin, sürüm ayarını 4.0.0.0'dan 2.0.0.0'a değiştirebilirsiniz. Benzer şekilde, kaynaklar ekli bir uygulama için **Çözüm Gezgini'yi** açın, Tüm Dosyaları Göster düğmesini seçin, **Project** (Visual Basic) veya Özellikler (C#) 'i genişletin ve ardından Visual Studio XML düzenleyicisinde *Resources.resx* dosyasını düzenleyin.   Sürüm ayarını 4.0.0.0 olarak 2.0.0.0 olarak değiştirebilirsiniz.

 Uygulamanıza simgeler, bit eşlemler veya veri bağlantısı dizeleri gibi ayarlar gibi kaynaklar varsa, **Project Tasarımcısı'nın** **Ayarlar** sayfasındaki tüm öğeleri kaldırarak ve ardından gerekli ayarları yeniden ekleyerek de hatayı çözebilirsiniz.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Projeyi farklı bir sürüme yeniden hedeflediniz .NET Framework ve başvurular çözümlemezse

 Bir projeyi farklı bir sürüme yeniden hedefler .NET Framework, başvurularınız bazı durumlarda düzgün çözümleyemeyebilir. Derlemelere açık tam başvurular genellikle bu soruna neden olur, ancak çözülen başvuruları kaldırarak ve sonra projeye geri ekleyerek bu sorunu çözesiniz. Alternatif olarak, başvuruları değiştirmek için proje dosyasını düzenleyebilirsiniz. İlk olarak, aşağıdaki formun başvurularını kaldırırız:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Ardından bunları basit biçimle değiştirirsiniz:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> Projenizi kapatıp yeniden açtıktan sonra, tüm başvuruların doğru çözümlene emin olmak için projeyi de yeniden oluşturmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl .NET Framework: .NET Framework](../ide/visual-studio-multi-targeting-overview.md)
- [.NET Framework profili oluşturma](/dotnet/framework/deployment/client-profile)
- [Çerçeve hedeflemeye genel bakış](../ide/visual-studio-multi-targeting-overview.md)
- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
