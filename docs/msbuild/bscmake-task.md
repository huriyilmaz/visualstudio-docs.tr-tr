---
title: BscMake Görev | Microsoft Dokümanlar
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77634519"
---
# <a name="bscmake-task"></a>BscGörev yap

> [!IMPORTANT]
> BscMake artık Visual Studio IDE tarafından kullanılmaz. Visual Studio 2008'den bu yana, göz atma bilgileri *Solution* klasöründeki bir *.sdf* dosyasında otomatik olarak depolanır.

 Microsoft Gözatma Bilgi Bakım Programı aracını sarar (*bscmake.exe*).  *bscmake.exe* aracı derleme sırasında oluşturulan kaynak tarayıcı dosyalarından *(.sbr)* bir gözatma bilgi dosyası (*.bsc*) oluşturur. *.bsc* dosyasını görüntülemek için **Nesne Tarayıcısını** kullanın. Daha fazla bilgi için [BSCMAKE referansına](/cpp/build/reference/bscmake-reference)bakın.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **BscMake** görevinin parametreleri açıklanmaktadır. Görev parametrelerinin çoğu komut satırı seçeneğine karşılık gelir.

|Parametre|Açıklama|
|---------------|-----------------|
|**Ek Seçenekler**|İsteğe bağlı **String** parametresi.<br /><br /> Komut satırında belirtilen seçenekler listesi. Örneğin, /\<option1\<> /\<option2> / seçenek #>. Başka bir **BscMake** görev parametresi tarafından temsil edilmeyen seçenekleri belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerindeki](/cpp/build/reference/bscmake-options)seçeneklere bakın.|
|**Outputfile**|İsteğe bağlı **String** parametresi.<br /><br /> Varsayılan çıktı dosya adını geçersiz kılan bir dosya adı belirtir.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerindeki](/cpp/build/reference/bscmake-options) **/o** seçeneğine bakın.|
|**PreserveSBR**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer, `true`bir nonincremental yapı zorlar. Tam, yeni bir *yapı,.bsc* dosyasının var olup olmadığına bakılmaksızın oluşur ve *.sbr* dosyalarının kesildikten öncesini engeller.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerindeki](/cpp/build/reference/bscmake-options) **/n** seçeneğine bakın.|
|**Kaynak**|İsteğe bağlı **ITaskItem[]** parametresi.<br /><br /> Görevler tarafından tüketilebilen ve yayılabilen bir dizi MSBuild kaynak dosya öğesi tanımlar.|
|**BastırmaBaşlangıç Banner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer, `true`görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerindeki](/cpp/build/reference/bscmake-options) **/NOLOGO** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe bağlı **String** parametresi.<br /><br /> İzleyici günlüğüiçin dizini belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
