---
title: WPF MSBuild görev başvurusu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eb21495954801d55c1db0bb9156a813ab73db683
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687085"
---
# <a name="wpf-msbuild-task-reference"></a>WPF MSBuild Görev Başvurusu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Presentation Foundation (WPF) derleme işlemi, Microsoft Build Engine 'i (MSBuild), biçimlendirme ve işlem kaynaklarını derlemeye yönelik görevler de dahil olmak üzere ek bir yapı görevi kümesiyle genişletir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [FileClassifier](../msbuild/fileclassifier-task.md)  
 Bir kaynak kaynakları kümesini bir derlemeye katıştırılacak şekilde sınıflandırır. Bir kaynak yerelleştirilebilir değilse, ana uygulama derlemesine katıştırılır; Aksi halde, bir uydu derlemesine katıştırılır.  
  
 [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md)  
 Bir projede en az bir [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] sayfa bu projede yerel olarak tanımlanan bir türe başvuruyorsa bir derleme oluşturur. Oluşturulan derleme, derleme işlemi tamamlandıktan sonra veya yapı işlemi başarısız olursa kaldırılır.  
  
 [GetWinFXPath](../msbuild/getwinfxpath-task.md)  
 Geçerli [!INCLUDE[TLA#tla_winfx](../includes/tlasharptla-winfx-md.md)] çalışma zamanının dizinini döndürür.  
  
 [MarkupCompilePass1](../msbuild/markupcompilepass1-task.md)  
 Yerelleştirilemeyen [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] Proje dosyalarını derlenmiş ikili biçime dönüştürür.  
  
 [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md)  
 [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)]Aynı projedeki türlere başvuran dosyalarda ikinci geçiş biçimlendirme derlemesini gerçekleştirir.  
  
 [MergeLocalizationDirectives](../msbuild/mergelocalizationdirectives-task.md)  
 Bir veya daha fazla ikili biçim dosyasının yerelleştirme özniteliklerini ve açıklamalarını [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] tüm derleme için tek bir dosyada birleştirir.  
  
 [ResourcesGenerator](../msbuild/resourcesgenerator-task.md)  
 Bir veya daha fazla kaynağı (. jpg,. ico,. bmp, [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] ikili biçimi ve diğer uzantı türlerini) bir. resources dosyasına katıştırır.  
  
 [UidManager](../msbuild/uidmanager-task.md)  
 Kaynak dosyalara dahil olan tüm öğeleri yerelleştirmek için, benzersiz tanımlayıcıları (UID 'ler) denetler, güncelleştirir veya kaldırır [!INCLUDE[TLA#tla_xaml](../includes/tlasharptla-xaml-md.md)] [!INCLUDE[TLA2#tla_xaml](../includes/tla2sharptla-xaml-md.md)] .  
  
 [UpdateManifestForBrowserApplication](../msbuild/updatemanifestforbrowserapplication-task.md)  
 **\<hostInBrowser />** Bir proje oluşturulduğunda, öğesini uygulama bildirimine (*ProjectName*. exe. manifest) ekler [!INCLUDE[TLA#tla_xbap](../includes/tlasharptla-xbap-md.md)] .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MSBUILD](https://msdn.microsoft.com/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)
