---
title: Sorun Giderme .NET Çerçeve Hedefleme Hataları | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1c496fd457e80220bb2ea4a2f032cef9508d9dcb
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631607"
---
# <a name="troubleshoot-net-framework-targeting-errors"></a>Sorun Giderme .NET Framework hedefleme hataları

Bu konu, başvuru sorunları nedeniyle oluşabilecek MSBuild hatalarını ve bu hataları nasıl çözebileceğinizi açıklar.

## <a name="you-have-referenced-a-project-or-assembly-that-targets-a-different-version-of-the-net-framework"></a>.NET Framework'ün farklı bir sürümünü hedefleyen bir proje veya derlemeye başvurulmuşsunuz

 .NET Framework'ün farklı sürümlerini hedefleyen projelere veya derlemelere başvuran uygulamalar oluşturabilirsiniz. Örneğin, .NET Framework 4 için istemci profilini hedefleyen ancak .NET Framework 2.0'ı hedefleyen bir derlemeye başvuran bir uygulama oluşturabilirsiniz. Ancak, .NET Framework'ün önceki bir sürümünü hedefleyen bir proje oluşturursanız, bu projede .NET Framework 4 veya .NET Framework 4'ün istemci profilini hedefleyen bir proje veya derlemeye başvuruda bulunamazsınız. Hatayı gidermek için, uygulamanızın başvurulan projeler veya derlemeler tarafından hedeflenen profille uyumlu bir profili veya profilleri hedefaldığından emin olun.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework"></a>Bir projeyi .NET Framework'ün farklı bir sürümüne yeniden hedeflediniz

 Uygulamanız için .NET Framework'ün hedef sürümünü değiştirirseniz, Visual Studio bazı başvuruları değiştirir, ancak bazı başvuruları el ile güncelleştirmeniz gerekebilir. Örneğin, bir uygulamayı .NET Framework 3.5 Hizmet Paketi 1'i hedeflemek üzere değiştirirseniz ve bu uygulamanın .NET Framework 4'ün istemci profiline dayanan kaynakları veya ayarları varsa, daha önce bahsedilen hatalardan biri oluşabilir.

 Uygulama ayarlarını aşmak için **Solution Explorer'ı**açın, **Tüm Dosyaları Göster'i**seçin ve ardından Visual Studio'nun XML düzenleyicisinde *app.config* dosyasını edin. Ayarlardaki sürümü .NET Framework'ün uygun sürümüyle eşleşecek şekilde değiştirin. Örneğin, sürüm ayarını 4.0.0.0'dan 2.0.0.0'a değiştirebilirsiniz. Benzer şekilde, kaynak ekleyen bir uygulama **için, Solution Explorer'ı**açın, **Tüm Dosyaları Göster** düğmesini seçin, Projemi (Visual Basic) veya **Özelliklerimi** (C#) genişletin ve Visual Studio'nun XML düzenleyicisinde *Resources.resx* dosyasını edin. **Properties** Sürüm ayarını 4.0.0.0'dan 2.0.0.0'a değiştirin.

 Uygulamanızda simgeler veya bit eşlemler veya veri bağlantısı dizeleri gibi ayarlar gibi kaynaklar varsa, **Proje Tasarımcısı'nın** **Ayarlar** sayfasındaki tüm öğeleri kaldırıp gerekli ayarları yeniden ekleyerek hatayı da çözebilirsiniz.

## <a name="you-have-re-targeted-a-project-to-a-different-version-of-the-net-framework-and-references-do-not-resolve"></a>Bir projeyi .NET Framework'ün farklı bir sürümüne yeniden hedeflediniz ve başvurular çözümlenmiyor

 Bir projeyi .NET Framework'ün farklı bir sürümüne yeniden hedefliyorsanız, başvurularınız bazı durumlarda düzgün şekilde çözülmeyebilir. Derlemelere yapılan açık tam nitelikli başvurular genellikle bu soruna neden olur, ancak çözümlenmeyen başvuruları kaldırıp projeye geri ekleyerek bunu çözebilirsiniz. Alternatif olarak, başvuruları değiştirmek için proje dosyasını değiştirebilirsiniz. İlk olarak, aşağıdaki formun başvurularını kaldırırsınız:

```xml
<Reference Include="System.ServiceModel, Version=3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089, processorArchitecture=MSIL" />
```

 Sonra onları basit bir formla değiştirirsin:

```xml
<Reference Include="System.ServiceModel" />
```

> [!NOTE]
> Projenizi kapatıp yeniden açtıktan sonra, tüm başvuruların doğru şekilde çözülmesini sağlamak için projeyi yeniden oluşturmanız gerekir.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılı: .NET Framework'ün bir sürümünü hedefleme](../ide/visual-studio-multi-targeting-overview.md)
- [.NET Framework istemci profili](/dotnet/framework/deployment/client-profile)
- [Çerçeve hedeflemegenel bakış](../ide/visual-studio-multi-targeting-overview.md)
- [Çoklu Sürüm Desteği](../msbuild/msbuild-multitargeting-overview.md)
