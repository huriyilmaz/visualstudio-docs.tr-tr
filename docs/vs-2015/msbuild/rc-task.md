---
title: RC görevi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
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
- RC task (MSBuild (Visual C++))
- MSBuild (Visual C++), RC task
ms.assetid: 2fd26c75-a056-4dda-9f7e-2f90d3748d88
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 81f64ec9774410ea55897445836c8633fe98e7bb
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/10/2020
ms.locfileid: "75851739"
---
# <a name="rc-task"></a>RC Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft Windows Kaynak derleyicisi aracı RC. exe ' yi sarmalanmış. **RC** görevi, imleçler, simgeler, bit eşlemler, iletişim kutuları ve yazı tipleri gibi kaynakları bir kaynak (. res) dosyasına derler. Daha fazla bilgi için [MSDN](https://msdn.microsoft.com/) Web sitesindeki "kaynak derleyicisi" konusuna bakın.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda RCtask parametreleri açıklanmaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelir.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|İsteğe bağlı **dize []** parametresi.<br /><br /> İçerme dosyaları için aranan dizinler listesine bir dizin ekler.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) bölümündeki **/i** seçeneğine bakın.|  
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırı optioncursor örneği, **"** _/option1/option2/option #_ " listesi. Başka bir **RC** görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) içindeki seçeneklere bakın.|  
|**Ayarı**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaynaklarda kullanılan kültürü temsil eden bir yerel ayar KIMLIĞI belirtir.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) bölümündeki **/l** seçeneğine bakın.|  
|**IgnoreStandardIncludePath**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, Kaynak derleyicinin üstbilgi dosyalarını veya kaynak dosyalarını ararken ıNCLUDE ortam değişkenini denetlemesini önler.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) bölümündeki **/x** seçeneğine bakın.|  
|**NullTerminateStrings**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, null-dize tablosundaki tüm dizeleri sonlandırır.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) bölümündeki **/n** seçeneğine bakın.|  
|**PreprocessorDefinitions**|İsteğe bağlı **dize []** parametresi.<br /><br /> Kaynak derleyicisi için bir veya daha fazla önişlemci sembolü tanımlayın. Makro sembolleri listesini belirtin.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) bölümündeki **/d** seçeneğine bakın. Ayrıca bu tablodaki **UndefinePreprocessorDefinitions** bölümüne bakın.|  
|**ResourceOutputFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaynak dosyasının adını belirtir. Bir kaynak dosyası adı belirtin.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) bölümündeki **/fo** seçeneğine bakın.|  
|**ShowProgress**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, derleyicinin ilerlemesini rapor eden iletileri görüntüler.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) içindeki **/v** seçeneğine bakın.|  
|**Kaynak**|Gerekli `ITaskItem[]` parametresi.<br /><br /> Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.|  
|**SuppressStartupBanner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için **/?** yazın. komut satırı seçeneği ve sonra **/nologo** seçeneğine bakın.|  
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlük dizinini belirtir.|  
|**UndefinePreprocessorDefinitions**|Önişlemci sembolünü tanımlama.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://msdn.microsoft.com/library/aa381055(VS.85).aspx) bölümündeki **/u** seçeneğine bakın. Ayrıca bkz. bu tablodaki **PreprocessorDefinitions** .|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)
