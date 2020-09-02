---
title: BscMake görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: reference
f1_keywords:
- vc.task.bscmake
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- MSBuild (Visual C++), tasks
- BscMake task (MSBuild (Visual C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7ed246255fc20b9660d24f234767fdeb451102f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65684542"
---
# <a name="bscmake-task"></a>BscMake Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ÖNEMLI
> BSCMAKE artık Visual Studio IDE tarafından kullanılmıyor. Visual Studio 2008 ' den itibaren, tarama bilgileri çözüm klasöründeki bir. sdf dosyasında otomatik olarak depolanır.  
  
 Microsoft 'A ait bilgi Bakımı yardımcı programı aracını (bscmake.exe) sarar.  bscmake.exe Aracı, derleme sırasında oluşturulan kaynak tarayıcı dosyalarından (. sbr) bir gözatma bilgi dosyası (. bsc) oluşturur. Bir. bsc dosyasını görüntülemek için **nesne tarayıcısı** kullanın. Daha fazla bilgi için bkz. [BSCMAKE başvurusu](https://msdn.microsoft.com/library/b97ad994-1355-4809-98db-6abc12c6fb13).  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda **BSCMAKE** görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi bir komut satırı seçeneğine karşılık gelir.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırında belirtilen seçeneklerin listesi. Örneğin, "/*Seçenek1*  / *Seçenek2*  / *seçenek #*". Başka bir **BSCMAKE** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerindeki](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2)seçeneklere bakın.|  
|**Çıktı**|İsteğe bağlı **dize** parametresi.<br /><br /> Varsayılan çıkış dosyası adını geçersiz kılan bir dosya adı belirtir.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerinde](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2) **/o** seçeneğine bakın.|  
|**PreserveSBR**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, Artımlı olmayan bir derlemeyi zorlar. Tam, artımlı olmayan bir derleme, bir. bsc dosyasının var olup olmadığına bakılmaksızın oluşur ve. sbr dosyalarının kesilmelerini engeller.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerinde](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2) **/n** seçeneğine bakın.|  
|**Kaynaklar**|İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.|  
|**SuppressStartupBanner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerinde](https://msdn.microsoft.com/library/fa2f1e06-c684-41cf-80dd-6a554835ebd2) **/nologo** seçeneğine bakın.|  
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlüğü için dizini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev başvurusu](../msbuild/msbuild-task-reference.md)
