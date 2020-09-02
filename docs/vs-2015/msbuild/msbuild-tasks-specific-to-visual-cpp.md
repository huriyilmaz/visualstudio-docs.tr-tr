---
title: Visual C++ 'e özgü MSBuild görevleri | Microsoft Docs
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
- MSBuild, tasks specific to Visual C++
ms.assetid: 05410f0c-7356-4692-bc00-20664421c9ff
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 452c3b408ab6471963124e61bc803e99eb6be80d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686915"
---
# <a name="msbuild-tasks-specific-to-visual-c"></a>Visual C++'ye Özgü MSBuild Görevleri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Görevler, derleme işlemi sırasında çalışan kodu sağlar. Visual C++ yüklendiğinde, ile birlikte yüklenenlere ek olarak aşağıdaki görevler kullanılabilir [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] . Daha fazla bilgi için bkz. [MSBuild (Visual C++) genel bakış](https://msdn.microsoft.com/library/dd258f6f-ab51-48d9-b274-f7ba911d05ca).  
  
 Her görevin parametrelerine ek olarak, her görevin aşağıdaki parametreleri de vardır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|`Condition`|İsteğe bağlı `String` parametre.<br /><br /> `Boolean` [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] Altyapının bu görevin yürütülüp yürütülmeyeceğini belirlemede kullandığı bir ifade. Tarafından desteklenen koşullar hakkında daha fazla bilgi için [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] bkz. [koşullar](../msbuild/msbuild-conditions.md).|  
|`ContinueOnError`|İsteğe bağlı parametre. , Aşağıdaki değerlerden birini içerebilir:<br /><br /> -   **WarnAndContinue** veya **true**. Bir görev başarısız olduğunda, [hedef](../msbuild/target-element-msbuild.md) öğe ve yapı içindeki sonraki görevler yürütülmeye devam eder ve görevdeki tüm hatalar uyarı olarak kabul edilir<br />-   **Errportadcontinue**. Bir görev başarısız olduğunda, öğedeki sonraki görevler `Target` ve derleme yürütülmeye devam eder ve görevdeki tüm hatalar hata olarak değerlendirilir.<br />-   **Errportadstop** veya **false** (varsayılan). Bir görev başarısız olduğunda, öğe ve yapı içindeki kalan görevler `Target` yürütülmez ve tüm `Target` öğe ve derleme başarısız olarak kabul edilir.<br /><br /> 4,5 ' den önceki .NET Framework sürümleri yalnızca `true` ve değerlerini destekliyordu `false` .<br /><br /> Daha fazla bilgi için bkz. [nasıl yapılır: görevlerdeki hataları yoksayma](../msbuild/how-to-ignore-errors-in-tasks.md).|  
  
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[BscMake görevi](../msbuild/bscmake-task.md)|Microsoft 'A ait bilgi Bakımı yardımcı programı aracını (bscmake.exe) sarar.|  
|[CL görevi](../msbuild/cl-task.md)|Visual C++ derleyici aracını sarmalanmış (cl.exe).|  
|[CPPClean görevi](../msbuild/cppclean-task.md)|Bir Visual C++ projesi oluşturulduğunda MSBuild tarafından oluşturulan geçici dosyaları siler.|  
|[LıB görevi](../msbuild/lib-task.md)|Microsoft 32-bit kitaplık Yöneticisi aracını (lib.exe) sarmalanmış olarak kaydırır.|  
|[Bağlantı görevi](../msbuild/link-task.md)|Visual C++ bağlayıcı aracını (link.exe) kaydırır.|  
|[MıDL görevi](../msbuild/midl-task.md)|Microsoft Arabirim Tanımlama Dili (MıDL) derleyici aracını (midl.exe) sarmalanmış.|  
|[MT görevi](../msbuild/mt-task.md)|Microsoft bildirim aracı 'nı (mt.exe) sarmalanmış.|  
|[RC görevi](../msbuild/rc-task.md)|Microsoft Windows Kaynak derleyicisi aracı 'nı (rc.exe) kaydırır.|  
|[SetEnv Görevi](../msbuild/setenv-task.md)|Belirtilen ortam değişkeninin değerini ayarlar veya siler.|  
|[VCMessage görevi](../msbuild/vcmessage-task.md)|Bir derleme sırasında uyarı iletilerini ve hata iletilerini günlüğe kaydeder.|  
|[XDCMake görevi](../msbuild/xdcmake-task.md)|XML belge açıklaması (. xdc) dosyalarını bir. xml dosyasında birleştiren XML belge aracı 'nı (xdcmake.exe) sarmalanmış hale gelir.|  
|[XSD görevi](../msbuild/xsd-task.md)|Bir kaynaktan şema veya sınıf dosyaları üreten XML şema tanımı aracını (xsd.exe) sarmalanmış olarak kaydırır.|  
|[MSBuild başvurusu](../msbuild/msbuild-reference.md)|MSBuild sisteminin öğelerini açıklar.|  
|[Görevler](../msbuild/msbuild-tasks.md)|Bir yapı oluşturmak için birleştirilebilecek kod birimleri olan görevleri açıklar.|  
|[Görev yazma](../msbuild/task-writing.md)|Bir görevin nasıl oluşturulacağını açıklar.|
