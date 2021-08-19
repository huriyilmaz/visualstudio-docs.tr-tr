---
title: BscMake Görev | Microsoft Docs
description: Microsoft Göz Atma Bilgileri Bakım Yardımcı Programı aracını sarmalanmış BscMake hakkında bilgi bscmake.exe. IDE Visual Studio artık BscMake kullanmaz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: f979a8f9e704dc689b2c176b2ce1356040e5c027
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085291"
---
# <a name="bscmake-task"></a>BscMake görevi

> [!IMPORTANT]
> BscMake artık IDE tarafından Visual Studio kullanılmaz. 2008 Visual Studio, göz atma bilgileri çözüm klasöründeki *bir .sdf* dosyasında otomatik *olarak* depolanır.

 Microsoft Gözatma Bilgileri Bakım Yardımcı Programı aracını sarmalar (*bscmake.exe*).  Bu *bscmake.exe* aracı, derleme sırasında oluşturulan kaynak tarayıcı dosyalarından (*.sbr*) bir göz atma bilgi dosyası (*.bsc)* derler. *Bir .bsc* dosyasını görüntülemek için Object **Browser'i** kullanın. Daha fazla bilgi için bkz. [BSCMAKE başvurusu.](/cpp/build/reference/bscmake-reference)

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda **BscMake görevinin parametreleri açık** almaktadır. Çoğu görev parametresi bir komut satırı seçeneğine karşılık gelen bir komut satırı seçeneğidir.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalOptions**|İsteğe **bağlı Dize** parametresi.<br /><br /> Komut satırda belirtilen seçeneklerin listesi. Örneğin, / \<option1>  / \<option2>  / \<option#> . Başka bir **BscMake** görev parametresi tarafından temsil etmeyen seçenekleri belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için [BSCMAKE seçenekleri'nde yer alan seçeneklere bakın.](/cpp/build/reference/bscmake-options)|
|**Outputfile**|İsteğe **bağlı Dize** parametresi.<br /><br /> Varsayılan çıkış dosyası adını geçersiz kılmak için bir dosya adı belirtir.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerinde](/cpp/build/reference/bscmake-options) **/o** seçeneğine bakın.|
|**PreserveSBR**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` bir nonincremental derlemeyi güçler. Bir *.bsc* dosyasının mevcut olup olmadığı önemli olmayan tam derlemeler oluşur ve *.sbr* dosyalarının kesilmesini önler.<br /><br /> Daha fazla bilgi için [BSCMAKE seçeneklerinde](/cpp/build/reference/bscmake-options) **/n** seçeneğine bakın.|
|**Kaynaklar**|İsteğe **bağlı ITaskItem[]** parametresi.<br /><br /> Görevler tarafından tüketilebilir MSBuild kaynak dosya öğeleri içeren bir dizi tanımlar.|
|**SuppressStartupBanner**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` görev başlatıldığında telif hakkı ve sürüm numarası iletinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için [BSCMAKE](/cpp/build/reference/bscmake-options) **seçeneklerinde /NOLOGO** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe **bağlı Dize** parametresi.<br /><br /> İzleyici günlüğünün dizinini belirtir.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)
