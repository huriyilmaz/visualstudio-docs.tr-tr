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
ms.openlocfilehash: ea44b7b98cce9bcb634217f504ea1f0529a2cf15
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298958"
---
# <a name="rc-task"></a>RC Görevi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Microsoft Windows Kaynak derleyicisi aracı RC. exe ' yi sarmalanmış. **RC** görevi, imleçler, simgeler, bit eşlemler, iletişim kutuları ve yazı tipleri gibi kaynakları bir kaynak (. res) dosyasına derler. Daha fazla bilgi için [MSDN](https://go.microsoft.com/fwlink/?LinkId=737) Web sitesindeki "kaynak derleyicisi" konusuna bakın.  
  
## <a name="parameters"></a>Parametreler  
 Aşağıdaki tabloda RCtask parametreleri açıklanmaktadır. Çoğu görev parametresi ve birkaç parametre kümesi, bir komut satırı seçeneğine karşılık gelir.  
  
|Parametre|Açıklama|  
|---------------|-----------------|  
|**AdditionalIncludeDirectories**|İsteğe bağlı **dize []** parametresi.<br /><br /> İçerme dosyaları için aranan dizinler listesine bir dizin ekler.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://go.microsoft.com/fwlink/?LinkId=155730) bölümündeki **/i** seçeneğine bakın.|  
|**AdditionalOptions**|İsteğe bağlı **dize** parametresi.<br /><br /> Komut satırı optioncursor örneği, **"** _/option1/option2/option #_ " listesi. Başka bir **RC** görev parametresi tarafından temsil edilmeyen komut satırı seçeneklerini belirtmek için bu parametreyi kullanın.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://go.microsoft.com/fwlink/?LinkId=155730) içindeki seçeneklere bakın.|  
|**Ayarı**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaynaklarda kullanılan kültürü temsil eden bir yerel ayar KIMLIĞI belirtir.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://go.microsoft.com/fwlink/?LinkId=155730) bölümündeki **/l** seçeneğine bakın.|  
|**Ignorestandardincludepath**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, Kaynak derleyicinin üstbilgi dosyalarını veya kaynak dosyalarını ararken ıNCLUDE ortam değişkenini denetlemesini önler.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://go.microsoft.com/fwlink/?LinkId=155730) bölümündeki **/x** seçeneğine bakın.|  
|**NullTerminateStrings**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, null-dize tablosundaki tüm dizeleri sonlandırır.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://go.microsoft.com/fwlink/?LinkId=155730) bölümündeki **/n** seçeneğine bakın.|  
|**PreprocessorDefinitions**|İsteğe bağlı **dize []** parametresi.<br /><br /> Kaynak derleyicisi için bir veya daha fazla önişlemci sembolü tanımlayın. Makro sembolleri listesini belirtin.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://go.microsoft.com/fwlink/?LinkId=155730) bölümündeki **/d** seçeneğine bakın. Ayrıca bu tablodaki **UndefinePreprocessorDefinitions** bölümüne bakın.|  
|**ResourceOutputFileName**|İsteğe bağlı **dize** parametresi.<br /><br /> Kaynak dosyasının adını belirtir. Bir kaynak dosyası adı belirtin.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://go.microsoft.com/fwlink/?LinkId=155730) bölümündeki **/fo** seçeneğine bakın.|  
|**ShowProgress**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, derleyicinin ilerlemesini rapor eden iletileri görüntüler.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://go.microsoft.com/fwlink/?LinkId=155730) içindeki **/v** seçeneğine bakın.|  
|**Kaynaktaki**|Gerekli `ITaskItem[]` parametresi.<br /><br /> Görevler tarafından tüketilen ve yayılmakta olabilecek bir MSBuild kaynak dosya öğeleri dizisini tanımlar.|  
|**SuppressStartupBanner**|İsteğe bağlı **Boolean** parametresi.<br /><br /> `true`, görev başladığında telif hakkı ve sürüm numarası iletisinin görüntülenmesini önler.<br /><br /> Daha fazla bilgi için **/?** yazın. komut satırı seçeneği ve sonra **/nologo** seçeneğine bakın.|  
|**TrackerLogDirectory**|İsteğe bağlı **dize** parametresi.<br /><br /> İzleyici günlük dizinini belirtir.|  
|**UndefinePreprocessorDefinitions**|Önişlemci sembolünü tanımlama.<br /><br /> Daha fazla bilgi için MSDN Web sitesindeki [RC (rc komut satırı) kullanma](https://go.microsoft.com/fwlink/?LinkId=155730) bölümündeki **/u** seçeneğine bakın. Ayrıca bkz. bu tablodaki **PreprocessorDefinitions** .|  
  
## <a name="remarks"></a>Açıklamalar  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Görev Başvurusu](../msbuild/msbuild-task-reference.md)
