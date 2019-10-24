---
title: RC görevi | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VC.Project.VCResourceCompilerTool.UndefineProcessorDefinitions
- vc.task.rc
- VC.Project.VCResourceCompilerTool.SuppressStartupBanner
- VC.Project.VCResourceCompilerTool.NullTerminateStrings
dev_langs:
- VB
- CSharp
- C++
- jsharp
- C++
helpviewer_keywords:
- RC task (MSBuild (C++))
- MSBuild (C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6d217ba46f7b50851c8fe19f420195dcf9ee698a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748046"
---
# <a name="rc-task"></a>RC görevi
Microsoft Windows Kaynak derleyicisi aracı *rc. exe*' yi sarmalanmış. **RC** görevi, imleçler, simgeler, bit eşlemler, iletişim kutuları ve yazı tipleri gibi kaynakları bir kaynak ( *. res*) dosyasına derler. Daha fazla bilgi için bkz. [kaynak derleyicisi](https://docs.microsoft.com/windows/desktop/menurc/resource-compiler).

## <a name="parameters"></a>Parametreler
 Aşağıdaki tabloda RC görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelir.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|İsteğe bağlı **dize []** parametresi.<br /><br /> İçerme dosyaları için aranan dizinler listesine bir dizin ekler.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730)içindeki **/i** seçeneğine bakın.|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırı seçeneklerinin listesi; Örneğin,/\<option1 >/\<option2 >/\<option # >. Başka bir **RC** görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730)içindeki seçeneklere bakın.|
|**Ayarı**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaynaklarda kullanılan kültürü temsil eden bir yerel ayar KIMLIĞI belirtir.<br /><br /> Daha fazla bilgi için RC kullanma bölümündeki **/l** SEÇENEĞINE [(rc komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730)bakın.|
|**Ignorestandardincludepath**|İsteğe bağlı **Boolean** parametresi.<br /><br /> @No__t_0, Kaynak derleyicinin üstbilgi dosyalarını veya kaynak dosyalarını ararken ıNCLUDE ortam değişkenini denetlemesini önler.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730)içindeki **/x** seçeneğine bakın.|
|**NullTerminateStrings**|İsteğe bağlı **Boolean** parametresi.<br /><br /> @No__t_0, null-dize tablosundaki tüm dizeleri sonlandırır.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730)içindeki **/n** seçeneğine bakın.|
|**PreprocessorDefinitions**|İsteğe bağlı **dize []** parametresi.<br /><br /> Kaynak derleyicisi için bir veya daha fazla önişlemci sembolü tanımlayın. Makro sembolleri listesini belirtin.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730)içindeki **/d** seçeneğine bakın. Ayrıca bu tablodaki **UndefinePreprocessorDefinitions** bölümüne bakın.|
|**ResourceOutputFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaynak dosyasının adını belirtir. Bir kaynak dosyası adı belirtin.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730)içindeki **/fo** seçeneğine bakın.|
|**ShowProgress**|İsteğe bağlı **Boolean** parametresi.<br /><br /> @No__t_0, derleyicinin ilerlemesini rapor eden iletileri görüntüler.<br /><br /> Daha fazla bilgi için RC kullanma içindeki **/v** SEÇENEĞINE [(rc komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730)bakın.|
|**Kaynaktaki**|Gerekli `ITaskItem[]` parametresi.<br /><br /> Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.|
|**SuppressStartupBanner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> @No__t_0, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için **/?** yazın. komut satırı seçeneği ve sonra **/nologo** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlük dizinini belirtir.|
|**UndefinePreprocessorDefinitions**|Önişlemci sembolünü tanımlama.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](http://go.microsoft.com/fwlink/?LinkId=155730)içindeki **/u** seçeneğine bakın. Ayrıca bkz. bu tablodaki **PreprocessorDefinitions** .|

## <a name="see-also"></a>Ayrıca bkz.
- [Görev başvurusu](../msbuild/msbuild-task-reference.md)