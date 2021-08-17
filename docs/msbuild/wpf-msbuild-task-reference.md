---
title: WPF MSBuild Görev Başvurusu | Microsoft Docs
description: Windows Presentation Foundation (WPF) derleme işlemi için görev başvurusuna bakın. Bu işlem, MSBuild görevlerle genişletmektedir.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 19a5fbd6da07648be784b155e3fb6b4dc4e78824
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122076972"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild görev başvurusu

Windows Presentation Foundation (WPF) derleme işlemi, işaretleme ve işlem kaynaklarını derleme görevleri de dahil olmak üzere Microsoft derleme altyapısını (MSBuild) ek bir derleme görevleri kümesiyle genişletmektedir.

## <a name="in-this-section"></a>Bu bölümde

- [FileClassifier](../msbuild/fileclassifier-task.md)

 Bir kaynak kaynak kümesi, bir derlemeye katıştıracak olan kaynak kümelerini sınıflar. Bir kaynak yerelleştirilebilir durumda değilse, ana uygulama derlemesine katıştırılabilir; aksi takdirde, bir uydu derlemesine gömülür.

- [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)

 Bir projedeki en az bir XAML sayfası, bu projede yerel olarak bildirilen bir türe başvurursa bir derleme üretir. Oluşturulan derleme, derleme işlemi tamamlandıktan sonra veya derleme işlemi başarısız olursa kaldırılır.

- [GetWinFXPath](../msbuild/getwinfxpath-task.md)

 Geçerli çalışma zamanının .NET Framework döndürür.

- [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)

 Yerelleştirilebilir olmayan XAML proje dosyalarını derlenmiş ikili biçime dönüştürür.

- [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)

 Aynı projedeki türlere başvuru yapan XAML dosyalarında ikinci geçiş işaretleme derlemesi gerçekleştirir.

- [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)

 Bir veya daha fazla XAML ikili biçim dosyasının yerelleştirme özniteliklerini ve açıklamalarını bütün derleme için tek bir dosyada birleştirilmesi.

- [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)

 Bir .resources dosyasına bir *veya daha fazla kaynak (.jpg*, *.ico*, *.bmp*, XAML ikili biçiminde ve diğer uzantı türleri) *katıştırır.*

- [UidManager](../msbuild/uidmanager-task.md)

 Kaynak XAML dosyalarına dahil edilen tüm XAML öğelerini yerelleştirmek için benzersiz tanımlayıcıları (UID) denetler, günceller veya kaldırır.

- [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)

 Bir XAML Tarayıcı Uygulaması (XBAP) projesi yerleşik olduğunda öğesini uygulama bildirimine **\<hostInBrowser />** (*\<projectname>.exe.manifest)* ekler.

## <a name="see-also"></a>Ayrıca bkz.

- [MSBuild](../msbuild/msbuild.md)