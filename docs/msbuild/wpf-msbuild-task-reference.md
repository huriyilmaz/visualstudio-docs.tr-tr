---
title: WPF MSBuild görev başvurusu | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77630853"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild görev başvurusu

Windows Presentation Foundation (WPF) derleme işlemi, Microsoft Build Engine 'i (MSBuild), biçimlendirme ve işlem kaynaklarını derlemeye yönelik görevler de dahil olmak üzere ek bir yapı görevi kümesiyle genişletir.

## <a name="in-this-section"></a>Bu bölümde

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Bir kaynak kaynakları kümesini bir derlemeye katıştırılacak şekilde sınıflandırır. Bir kaynak yerelleştirilebilir değilse, ana uygulama derlemesine katıştırılır; Aksi halde, bir uydu derlemesine katıştırılır.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Bir projede en az bir XAML sayfası bu projede yerel olarak tanımlanan bir türe başvuruyorsa bir derleme oluşturur. Oluşturulan derleme, derleme işlemi tamamlandıktan sonra veya yapı işlemi başarısız olursa kaldırılır.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Geçerli .NET Framework çalışma zamanının dizinini döndürür.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Yerelleştirilemeyen XAML proje dosyalarını derlenmiş ikili biçime dönüştürür.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Aynı projedeki türlere başvuran XAML dosyalarında ikinci geçiş biçimlendirme derlemesini gerçekleştirir.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Bir veya daha fazla XAML ikili biçim dosyasının yerelleştirme özniteliklerini ve açıklamalarını tüm derleme için tek bir dosyada birleştirir.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Bir veya daha fazla kaynağı (*. jpg*, *. ico*, *. bmp*, ikili biçimdeki XAML ve diğer uzantı türlerini) bir *. resources* dosyasına katıştırır.

- [UidManager](../msbuild/uidmanager-task.md)

 Kaynak XAML dosyalarında yer alan tüm XAML öğelerini yerelleştirmek için, benzersiz tanımlayıcıları (UID 'ler) denetler, güncelleştirir veya kaldırır.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 **\<hostInBrowser />** XAML tarayıcı uygulaması (XBAP) projesi yapılandırıldığında, öğesini uygulama bildirimine (* \<projectname> . exe. manifest*) ekler.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBUILD](../msbuild/msbuild.md)