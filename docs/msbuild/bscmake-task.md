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
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 668d42cdb0bc5cfb8dd344aab51ad0c66a838cd2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77634519"
---
# <a name="bscmake-task"></a>BscMake görevi

> [!IMPORTANT]
> BscMake artık Visual Studio IDE tarafından kullanılmıyor. Visual Studio 2008 ' den itibaren, tarama bilgileri *çözüm* klasöründeki bir *. sdf* dosyasında otomatik olarak depolanır.

 Microsoft 'A ait bilgi Bakımı yardımcı programı aracını (*bscmake.exe*) sarar.  *bscmake.exe* Aracı, derleme sırasında oluşturulan kaynak tarayıcı dosyalarından (.*SBR*) bir gözatma bilgi dosyası (*. bsc*) oluşturur. Bir *. bsc* dosyasını görüntülemek için **nesne tarayıcısı** kullanın. Daha fazla bilgi için bkz. [BSCMAKE başvurusu](/cpp/build/reference/bscmake-reference).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **BSCMAKE** görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi bir komut satırı seçeneğine karşılık gelir.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırında belirtilen seçeneklerin listesi. Örneğin,/ \<option1>  / \<option2>  / \<option#> . Başka bir **BSCMAKE** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerindeki](/cpp/build/reference/bscmake-options)seçeneklere bakın.|
|**Çıktı**|İsteğe bağlı **dize** parametresi.<br /><br /> Varsayılan çıkış dosyası adını geçersiz kılan bir dosya adı belirtir.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerinde](/cpp/build/reference/bscmake-options) **/o** seçeneğine bakın.|
|**PreserveSBR**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, Artımlı olmayan bir derlemeyi zorlar. Tam, artımlı olmayan bir derleme, bir *. bsc* dosyasının var olup olmadığına bakılmaksızın oluşur ve *. sbr* dosyalarının kesilmelerini engeller.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerinde](/cpp/build/reference/bscmake-options) **/n** seçeneğine bakın.|
|**Kaynaklar**|İsteğe bağlı **ıtaskitem []** parametresi.<br /><br /> Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.|
|**SuppressStartupBanner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerinde](/cpp/build/reference/bscmake-options) **/nologo** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlüğü için dizini belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
