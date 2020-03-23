---
title: WPF MSBuild Görev Referansı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- WPF MSBuild task reference [WPF MSBuild], term/definition table
- build tasks [WPF MSBuild], Microsoft build engine
- build tasks using the Microsoft build engine [WPF MSBuild], compile markup and process resources
- WPF MSBuild task reference [WPF MSBuild]
ms.assetid: 96df0370-e50f-4ffc-9771-b12fb8721143
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70d994e32b717ff566a2e38acee732c7525d1bb0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77630853"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild görev başvurusu

Windows Sunu Temeli (WPF) oluşturma işlemi, biçimlendirme ve işlem kaynaklarını derleme görevleri de dahil olmak üzere ek bir yapı görevi kümesiyle Microsoft yapı altyapısını (MSBuild) genişletir.

## <a name="in-this-section"></a>Bu bölümde

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Kaynak kaynakları kümesini derlemeye katıştırılmış kaynaklar olarak sınıflar. Bir kaynak yerelleştirilebilir değilse, ana uygulama derlemesine gömülür; aksi takdirde, bir uydu montajı içine gömülüdür.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Projedeki en az bir XAML sayfası, bu projede yerel olarak bildirilen bir türe başvuruyorsa, bir derleme oluşturur. Oluşturulan derleme, yapı işlemi tamamlandıktan sonra veya yapı işlemi başarısız olursa kaldırılır.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Geçerli .NET Framework çalışma zamanının dizini döndürür.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Yerelleştirilebilir olmayan XAML proje dosyalarını derlenmiş ikili biçime dönüştürür.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Aynı projede başvuru türlerine başvuran XAML dosyalarında ikinci geçiş biçimlendirme derlemesi gerçekleştirir.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Bir veya daha fazla XAML ikili biçimli dosyaların yerelleştirme özniteliklerini ve yorumlarını tüm derleme için tek bir dosyada birleştirir.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Bir veya daha fazla kaynağı *(.jpg*, *.ico*, *.bmp*, ikili biçimde XAML ve diğer uzantı türleri) *bir .resources* dosyasına yerzein.

- [UidManager](../msbuild/uidmanager-task.md)

 Kaynak XAML dosyalarında yer alan tüm XAML öğelerini yerelleştirmek için benzersiz tanımlayıcıları (UIEd'leri) denetler, güncelleştirir veya kaldırır.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Bir XAML Tarayıcı Uygulaması (XBAP) projesi inşa ** \<edildiğinde, hostInBrowser />** öğesini uygulama bildirimine*\<(projeadı>.exe.manifest)* ekler.

## <a name="see-also"></a>Ayrıca bkz.

- [Msbuild](../msbuild/msbuild.md)