---
title: Başvuru (Programlı yakalama) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8cebeb7eb651c11b5f560b981df30213fc726c66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162256"
---
# <a name="reference-programmatic-capture"></a>Başvuru (Programlı Yakalama)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Grafik Tanılama, Programlı yakalama API 'SI aracılığıyla yakalama özellikleri üzerinde programlama denetimini destekler. Bu API 'yi, grafik tanılama HUD (baş ekran) için ileti açıp eklemek, grafik günlük dosyalarını başlatıp oluşturmak ve grafik bilgilerini yakalamak için kullanabilirsiniz.  
  
## <a name="programmatic-capture-apis"></a>Programlı yakalama API 'Leri  
  
### <a name="classes"></a>Sınıflar  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[VsgDbg Sınıfı](../debugger/vsgdbg-class.md)|Grafik tanılama 'nın uygulama içi bileşeninin programlı olarak denetlendiği arabirimi temsil eder.|  
  
### <a name="preprocessor-symbols"></a>Önişlemci sembolleri  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[DONT_SAVE_VSGLOG_TO_TEMP](../debugger/dont-save-vsglog-to-temp.md)|Grafik günlük dosyasının kullanıcının geçici dosyalar dizinine kaydedilip kaydedilmediğini kendi varlığına göre tanımlar.|  
|[VSG_DEFAULT_RUN_FILENAME](../debugger/vsg-default-run-filename.md)|Grafik günlük dosyasının varsayılan dosya adını tanımlar.|  
|[VSG_NODEFAULT_INSTANCE](../debugger/vsg-nodefault-instance.md)|Sınıfının varsayılan bir örneğinin sağlandığına ilişkin varlığına göre tanımlar `VsgDbg` .|  
  
## <a name="related-articles"></a>İlgili Makaleler  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Grafik Bilgilerini Yakalama](../debugger/capturing-graphics-information.md)|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]İşleme sorunlarını tanılamak için grafik tanılama araçları kullanabilmeniz için, DirectX tabanlı uygulamanızdan grafik bilgilerinin nasıl yakalanacağını gösterir.|  
|[Genel Bakış](../debugger/overview-of-visual-studio-graphics-diagnostics.md)|Grafik Tanılama, DirectX oyunları ve uygulamalarında işleme hatalarında hata ayıklamanıza nasıl yardımcı olduğunu gösterir.|
