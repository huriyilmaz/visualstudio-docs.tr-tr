---
title: RC Görevi | Microsoft Dokümanlar
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 13ae844759cb73de6dc7bcce6c8898c21132f9d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632920"
---
# <a name="rc-task"></a>RC görevi

Microsoft Windows Kaynak Derleyici aracını sarar, *rc.exe*. **RC** görevi imleçler, simgeler, bit eşlemler, iletişim kutuları ve yazı tipleri gibi kaynakları bir kaynak (*.res*) dosyasında derler. Daha fazla bilgi için [Kaynak Derleyicisi'ne](/windows/desktop/menurc/resource-compiler)bakın.

## <a name="parameters"></a>Parametreler

 Aşağıdaki tabloda RC görevinin parametreleri açıklanmaktadır. Görev parametrelerinin çoğu ve birkaç parametre kümesi komut satırı seçeneğine karşılık gelir.

|Parametre|Açıklama|
|---------------|-----------------|
|**EkIncludeDirectories**|İsteğe bağlı **String[]** parametresi.<br /><br /> Aranan dizinler listesine bir dizin ekler.<br /><br /> Daha fazla bilgi için RC [(RC komut satırı) kullanma](/windows/win32/menurc/using-rc-the-rc-command-line-) **/I** seçeneğine bakın.|
|**Ek Seçenekler**|İsteğe bağlı **String** parametresi.<br /><br /> Komut satırı seçeneklerilistesi; örneğin, /\<option1\<> /\<option2> / seçenek #>. Başka bir **RC** görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için [RC (RC komut satırı) kullanma seçeneklerine](/windows/win32/menurc/using-rc-the-rc-command-line-)bakın.|
|**Kültür**|İsteğe bağlı **String** parametresi.<br /><br /> Kaynaklarda kullanılan kültürü temsil eden bir yerel kimlik belirtir.<br /><br /> Daha fazla bilgi için RC [(RC komut satırı) kullanma](/windows/win32/menurc/using-rc-the-rc-command-line-) **/l** seçeneğine bakın.|
|**StandartIncludePath'i YokSay**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer, `true`kaynak derleyicisi üstbilgi dosyaları veya kaynak dosyaları ararken INCLUDE ortamı değişkenini denetlemek engeller.<br /><br /> Daha fazla bilgi için RC [(RC komut satırı) kullanırken](/windows/win32/menurc/using-rc-the-rc-command-line-) **/x** seçeneğine bakın.|
|**NullTerminateStrings**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Dize `true`tablosundaki tüm dizeleri geçersiz kılarsa.<br /><br /> Daha fazla bilgi **/n** için RC [(RC komut satırı) kullanmaseçeneğine](/windows/win32/menurc/using-rc-the-rc-command-line-)bakın.|
|**Önİşleme İşlemci Tanımlar**|İsteğe bağlı **String[]** parametresi.<br /><br /> Kaynak derleyicisi için bir veya daha fazla önişlemci sembolü tanımlayın. Makro sembolleri listesini belirtin.<br /><br /> Daha fazla bilgi için RC [(RC komut satırı) kullanma](/windows/win32/menurc/using-rc-the-rc-command-line-) **/d** seçeneğine bakın. Ayrıca bu tabloda **TanımsızPreprocessorDefinitions** bakın.|
|**Kaynak ÇıktısıDosya Adı**|İsteğe bağlı **String** parametresi.<br /><br /> Kaynak dosyasının adını belirtir. Kaynak dosya adı belirtin.<br /><br /> Daha fazla bilgi için RC [(RC komut satırı) kullanmada](/windows/win32/menurc/using-rc-the-rc-command-line-) **/fo** seçeneğine bakın.|
|**İlerlemeyi Göster**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer, `true`derleyicinin ilerleme rapor iletileri görüntüler.<br /><br /> Daha fazla bilgi için RC [(RC komut satırı) kullanmada](/windows/win32/menurc/using-rc-the-rc-command-line-) **/v** seçeneğine bakın.|
|**Kaynak**|Gerekli `ITaskItem[]` parametre.<br /><br /> Görevler tarafından tüketilebilen ve yayılabilen bir dizi MSBuild kaynak dosya öğesi tanımlar.|
|**BastırmaBaşlangıç Banner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> Eğer, `true`görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini engeller.<br /><br /> Daha fazla bilgi için **,?** komut satırı seçeneği ve sonra **/nologo** seçeneğini görün.|
|**TrackerLogDirectory**|İsteğe bağlı **String** parametresi.<br /><br /> İzleyici günlük dizini belirtir.|
|**TanımsızPreprocessorDefinitions**|Önişlemci simgesini tanımdan tanımlayın.<br /><br /> Daha fazla bilgi için RC [(RC komut satırı) kullanma](/windows/win32/menurc/using-rc-the-rc-command-line-) **/u** seçeneğine bakın. Ayrıca bu tabloda **PreprocessorDefinitions** bakın.|

## <a name="see-also"></a>Ayrıca bkz.

- [Görev başvurusu](../msbuild/msbuild-task-reference.md)