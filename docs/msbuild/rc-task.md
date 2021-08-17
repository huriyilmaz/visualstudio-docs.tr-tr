---
title: RC Görev | Microsoft Docs
description: MSBuild microsoft Windows Kaynak Derleyicisi aracını sarmak için RC görevini nasıl kullandığını ve rc.exe bir .res dosyasına nasıl derlen olduğunu öğrenin.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077094"
---
# <a name="rc-task"></a>RC görevi

Microsoft Windows Kaynak Derleyicisi aracını sarmalar ve *rc.exe.* **RC görevi,** imleçler, simgeler, bit eşlemler, iletişim kutuları ve yazı tipleri gibi kaynakları bir kaynak (*.res*) dosyasına derler. Daha fazla bilgi için [bkz. Kaynak Derleyicisi.](/windows/desktop/menurc/resource-compiler)

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda RC görevinin parametreleri açık almaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelen bir seçenektir.

|Parametre|Açıklama|
|---------------|-----------------|
|**AdditionalIncludeDirectories**|İsteğe **bağlı String[]** parametresi.<br /><br /> Ekleme dosyaları için aranan dizinler listesine bir dizin ekler.<br /><br /> Daha fazla bilgi için BKZ. RC Kullanma [(RC komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içinde **/I** seçeneği.|
|**AdditionalOptions**|İsteğe **bağlı Dize** parametresi.<br /><br /> Komut satırı seçeneklerinin listesi; Örneğin, / \<option1>  / \<option2>  / \<option#> . Başka bir RC görev parametresi tarafından temsil etmeyen komut satırı seçeneklerini belirtmek için **bu** parametreyi kullanın.<br /><br /> Daha fazla bilgi için BKZ. [RC kullanma (RC komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-).|
|**Kültür**|İsteğe **bağlı Dize** parametresi.<br /><br /> Kaynaklarda kullanılan kültürü temsil eden bir yerel ayar kimliği belirtir.<br /><br /> Daha fazla bilgi için BKZ. RC Kullanma [(RC komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içinde **/l** seçeneği.|
|**IgnoreStandardIncludePath**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` kaynak derleyicinin üst bilgi dosyalarını veya kaynak dosyalarını ararken INCLUDE ortam değişkenlerini denetlemesini önler.<br /><br /> Daha fazla bilgi için BKZ. RC Kullanma [(RC komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içinde **/x** seçeneği.|
|**NullTerminateStrings**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` null-dize tablosunda tüm dizeleri sonlandırılır.<br /><br /> Daha fazla bilgi için BKZ. RC Kullanma [(RC komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içinde **/n** seçeneği.|
|**ÖnişlemciDefinitions**|İsteğe **bağlı String[]** parametresi.<br /><br /> Kaynak derleyicisi için bir veya daha fazla ön işlemci sembolü tanımlayın. Makro sembollerinin listesini belirtin.<br /><br /> Daha fazla bilgi için BKZ. RC Kullanma [(RC komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içinde **/d** seçeneği. Ayrıca bu **tabloda UndefinePreprocessorDefinitions'a** bakın.|
|**ResourceOutputFileName**|İsteğe **bağlı Dize** parametresi.<br /><br /> Kaynak dosyasının adını belirtir. Bir kaynak dosyası adı belirtin.<br /><br /> Daha fazla bilgi için BKZ. RC Kullanma [(RC komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içinde **/fo** seçeneği.|
|**ShowProgress**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` derleyicinin ilerleme durumuyla ilgili olarak rapor eden iletileri görüntüler.<br /><br /> Daha fazla bilgi için BKZ. RC Kullanma [(RC komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içinde **/v** seçeneği.|
|**Kaynak**|Gerekli `ITaskItem[]` parametre.<br /><br /> Görevler tarafından tüketilebilir MSBuild kaynak dosya öğeleri içeren bir dizi tanımlar.|
|**SuppressStartupBanner**|İsteğe **bağlı Boole parametresi.**<br /><br /> ise, `true` görev başlatıldığında telif hakkı ve sürüm numarası iletinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için **/? yazın.** komut satırı seçeneğine bakın ve **/nologo seçeneğine** bakın.|
|**TrackerLogDirectory**|İsteğe **bağlı Dize** parametresi.<br /><br /> İzleyici günlüğü dizinini belirtir.|
|**UndefinePreprocessorDefinitions**|Ön işlemci simgesinin tanımlarını geri anın.<br /><br /> Daha fazla bilgi için BKZ. RC Kullanma [(RC komut satırı)](/windows/win32/menurc/using-rc-the-rc-command-line-)içinde **/u** seçeneği. Ayrıca bu **tablodaki ÖnişlemciDefinitions'a** da bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)