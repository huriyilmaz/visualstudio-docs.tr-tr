---
title: RC görevi | Microsoft Docs
description: MSBuild, kaynakları bir. res dosyasında derlenen rc.exe Microsoft Windows kaynak derleyicisi aracını kaydırmak için RC görevini nasıl kullandığını öğrenin.
ms.custom: SEO-VS-2020
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 393e34bf68745df58f7f3e7dc4d45afb308c6c80
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726853"
---
# <a name="rc-task"></a>RC görevi

, *rc.exe* Microsoft Windows kaynak derleyicisi aracını sarmalanmış. **RC** görevi, imleçler, simgeler, bit eşlemler, iletişim kutuları ve yazı tipleri gibi kaynakları bir kaynak (*. res*) dosyasına derler. Daha fazla bilgi için bkz. [kaynak derleyicisi](/windows/desktop/menurc/resource-compiler).

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda RC görevinin parametreleri açıklanmaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelir.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|İsteğe bağlı **dize []** parametresi.<br /><br /> İçerme dosyaları için aranan dizinler listesine bir dizin ekler.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içindeki **/i** seçeneğine bakın.|
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırı seçeneklerinin listesi; Örneğin,/ \<option1>  / \<option2>  / \<option#> . Başka bir **RC** görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içindeki seçeneklere bakın.|
|**Kültür**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaynaklarda kullanılan kültürü temsil eden bir yerel ayar KIMLIĞI belirtir.<br /><br /> Daha fazla bilgi için RC kullanma bölümündeki **/l** SEÇENEĞINE [(rc komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)bakın.|
|**Ignorestandardincludepath**|İsteğe bağlı **Boolean** parametresi.<br /><br /> İse `true` , Kaynak derleyicinin üstbilgi dosyalarını veya kaynak dosyalarını ararken INCLUDE ortam değişkenini denetlemesini önler.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içindeki **/x** seçeneğine bakın.|
|**NullTerminateStrings**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer `true` , null-dize tablosundaki tüm dizeleri sonlandırır.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içindeki **/n** seçeneğine bakın.|
|**PreprocessorDefinitions**|İsteğe bağlı **dize []** parametresi.<br /><br /> Kaynak derleyicisi için bir veya daha fazla önişlemci sembolü tanımlayın. Makro sembolleri listesini belirtin.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içindeki **/d** seçeneğine bakın. Ayrıca bu tablodaki **UndefinePreprocessorDefinitions** bölümüne bakın.|
|**ResourceOutputFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaynak dosyasının adını belirtir. Bir kaynak dosyası adı belirtin.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içindeki **/fo** seçeneğine bakın.|
|**ShowProgress**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, Derleyicinin ilerlemesini rapor eden iletileri görüntüler.<br /><br /> Daha fazla bilgi için RC kullanma içindeki **/v** SEÇENEĞINE [(rc komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)bakın.|
|**Kaynak**|Gerekli `ITaskItem[]` parametre.<br /><br /> görevler tarafından tüketilen ve yayılan MSBuild kaynak dosya öğelerinin dizisini tanımlar.|
|**SuppressStartupBanner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> İse `true` , görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için **/?** yazın. komut satırı seçeneği ve sonra **/nologo** seçeneğine bakın.|
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlük dizinini belirtir.|
|**UndefinePreprocessorDefinitions**|Önişlemci sembolünü tanımlama.<br /><br /> Daha fazla bilgi için [RC kullanma (rc komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içindeki **/u** seçeneğine bakın. Ayrıca bkz. bu tablodaki **PreprocessorDefinitions** .|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)