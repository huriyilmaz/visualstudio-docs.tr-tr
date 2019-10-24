---
title: BscMake görevi | Microsoft Docs
ms.date: 11/04/2016
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
- MSBuild (C++), tasks
- BscMake task (MSBuild (C++))
ms.assetid: bb98fc67-cad8-43a7-9598-60df6d734db2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: acf9c0df17ec0e1bb97c1426d5d312f616de0a8e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72747379"
---
# <a name="bscmake-task"></a>BscMake görevi
> [!IMPORTANT]
> BscMake artık Visual Studio IDE tarafından kullanılmıyor. Visual Studio 2008 ' den itibaren, tarama bilgileri *çözüm* klasöründeki bir *. sdf* dosyasında otomatik olarak depolanır.

 Microsoft tarayıcı bilgi Bakımı yardımcı programı aracını (*bscmake. exe*) sarar.  *Bscmake. exe* Aracı, derleme sırasında oluşturulan kaynak tarayıcı dosyalarından (.*SBR*) bir gözatma bilgi dosyası ( *. bsc*) oluşturur. Bir *. bsc* dosyasını görüntülemek için **nesne tarayıcısı** kullanın. Daha fazla bilgi için bkz. [BSCMAKE başvurusu](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda **BSCMAKE** görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi bir komut satırı seçeneğine karşılık gelir.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırında belirtilen seçeneklerin listesi. Örneğin,/\<option1 >/\<option2 >/\<option # >. Başka bir **BSCMAKE** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerindeki](/cpp/build/reference/bscmake-options)seçeneklere bakın.|
|**Çıktı**|İsteğe bağlı **dize** parametresi.<br /><br /> Varsayılan çıkış dosyası adını geçersiz kılan bir dosya adı belirtir.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerinde](/cpp/build/reference/bscmake-options) **/o** seçeneğine bakın.|
|**PreserveSBR**|İsteğe bağlı **Boolean** parametresi.<br /><br /> @No__t_0, artımlı olmayan bir derlemeyi zorlar. Tam, artımlı olmayan bir derleme, bir *. bsc* dosyasının var olup olmadığına bakılmaksızın oluşur ve *. sbr* dosyalarının kesilmelerini engeller.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerinde](/cpp/build/reference/bscmake-options) **/n** seçeneğine bakın.|
|**Ğına**|İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.|
|**SuppressStartupBanner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> @No__t_0, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerinde](/cpp/build/reference/bscmake-options) **/nologo** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlüğü için dizini belirtir.|

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)