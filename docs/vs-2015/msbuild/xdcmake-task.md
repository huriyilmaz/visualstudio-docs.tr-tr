---
title: XDCMake görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.xdcmake
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- XDCMake task (MSBuild (Visual C++))
- MSBuild (Visual C++), XDCMake task
ms.assetid: a7de9c64-903a-4a02-85f3-f37672270f25
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c16c92b41aa0635ecb24d83e30e2c347620b2c75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675532"
---
# <a name="xdcmake-task"></a>XDCMake Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XML belge açıklaması (. xdc) dosyalarını bir. xml dosyasında birleştiren XML belge aracı 'nı (xdcmake.exe) sarmalanmış hale gelir.  
  
 Bir. xdc dosyası, Visual C++ kaynak kodunuzda belge açıklamaları sağladığınızda ve [/doc](https://msdn.microsoft.com/library/b54f7e2c-f28f-4f46-9ed6-0db09be2cc63) derleyici seçeneğini kullanarak derlemenizde oluşturulur. Daha fazla bilgi için, bkz. [XDCMake başvurusu](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [XML belge Oluşturucu aracı özellik sayfaları](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)ve xdcmake.exe için komut satırı yardım seçeneği (**/?**).  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, xdcmake.exe aracı birkaç komut satırı seçeneğini destekler. Ek seçenekler, **/Old** komut satırı seçeneğini belirttiğinizde desteklenir.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda **XDCMake** görevinin parametreleri açıklanmaktadır.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**AdditionalDocumentFile**|İsteğe bağlı **dize []** parametresi.<br /><br /> Birleştirilecek bir veya daha fazla ek. xdc dosyasını belirtir.<br /><br /> Daha fazla bilgi için [XML belge Oluşturucu aracı özellik sayfalarındaki](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0) **ek belge dosyaları** açıklamasına bakın. Ayrıca, xdcmake.exe için **/Old** ve **/FS** komut satırı seçeneklerine bakın.|  
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırında belirtilen seçeneklerin listesi. Örneğin, "*/option1/option2/option #*". Diğer bir **XDCMake** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için, bkz. [XDCMake başvurusu](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac), [XML belge Oluşturucu aracı özellik sayfaları](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0)ve xdcmake.exe için komut satırı yardımı (**/?**).|  
|**DocumentLibraryDependencies**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`Ve geçerli projenin çözümde bir statik kitaplık (. lib) projesine bağımlılığı varsa, bu kitaplık projesi için. xdc dosyaları geçerli proje için. xml dosya çıktısına dahil edilir.<br /><br /> Daha fazla bilgi için bkz. [XML belge Oluşturucu aracı özellik sayfalarındaki](https://msdn.microsoft.com/library/645912b5-197a-4c36-ba58-64df09444ca0) **belge kitaplığı bağımlılıkları** açıklaması.|  
|**Çıktı**|İsteğe bağlı **dize** parametresi.<br /><br /> Varsayılan çıkış dosyası adını geçersiz kılar. Varsayılan ad, işlenen ilk. xdc dosyasının adından türetilir.<br /><br /> Daha fazla bilgi için bkz **/out:** `filename` . [XDCMake başvurusu](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac)içindeki/Out: Option. Ayrıca, xdcmake.exe için **/Old** ve **/fo** komut satırı seçeneklerine bakın.|  
|**ProjectName**|İsteğe bağlı **dize** parametresi.<br /><br /> Geçerli projenin adı.|  
|**Slakıold**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Varsa `true` , ek xdcmake.exe seçeneklerini sunar.<br /><br /> Daha fazla bilgi için, xdcmake.exe için **/Old** komut satırı seçeneğine bakın.|  
|**Kaynaklar**|Gerekli `ITaskItem[]` parametre.<br /><br /> Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.|  
|**SuppressStartupBanner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için, [XDCMake başvurusunda](https://msdn.microsoft.com/library/14e65747-d000-4343-854b-8393bf01cbac) **/nologo** seçeneğine bakın.|  
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlüğü için dizini belirtir.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
