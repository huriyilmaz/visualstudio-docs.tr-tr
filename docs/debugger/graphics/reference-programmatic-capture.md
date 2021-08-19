---
title: Başvuru (Programlı yakalama) | Microsoft Docs
description: Grafik Tanılama yakalama özellikleri üzerinde programlı denetim sağlamak için programlı yakalama API 'sini kullanın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: ef60eb8d-1ac2-4e3a-9b4b-f6da0bdd9da8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 9d8f51a79f47889a1cad4c331c6fc941a6ddd2e4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122146983"
---
# <a name="reference-programmatic-capture"></a>Başvuru (Programlı Yakalama)
Grafik Tanılama, Programlı yakalama API 'SI aracılığıyla yakalama özellikleri üzerinde programlama denetimini destekler. Bu API 'yi, grafik tanılama HUD (baş ekran) için ileti açıp eklemek, grafik günlük dosyalarını başlatıp oluşturmak ve grafik bilgilerini yakalamak için kullanabilirsiniz.

## <a name="programmatic-capture-apis"></a>Programlı yakalama API 'Leri

### <a name="classes"></a>Sınıflar

|Ad|Açıklama|
|----------|-----------------|
|[VsgDbg Sınıfı](vsgdbg-class.md)|Grafik tanılama 'nın uygulama içi bileşeninin programlı olarak denetlendiği arabirimi temsil eder.|

### <a name="preprocessor-symbols"></a>Önişlemci sembolleri

|Ad|Açıklama|
|----------|-----------------|
|[DONT_SAVE_VSGLOG_TO_TEMP](dont-save-vsglog-to-temp.md)|Grafik günlük dosyasının kullanıcının geçici dosyalar dizinine kaydedilip kaydedilmediğini kendi varlığına göre tanımlar.|
|[VSG_DEFAULT_RUN_FILENAME](vsg-default-run-filename.md)|Grafik günlük dosyasının varsayılan dosya adını tanımlar.|
|[VSG_NODEFAULT_INSTANCE](vsg-nodefault-instance.md)|Sınıfının varsayılan bir örneğinin sağlandığına ilişkin varlığına göre tanımlar `VsgDbg` .|

## <a name="related-articles"></a>İlgili Makaleler

| Başlık | Açıklama |
| - | - |
| [Grafik Bilgilerini Yakalama](capturing-graphics-information.md) | [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]İşleme sorunlarını tanılamak için grafik tanılama araçları kullanabilmeniz için, DirectX tabanlı uygulamanızdan grafik bilgilerinin nasıl yakalanacağını gösterir. |
| [Genel Bakış](overview-of-visual-studio-graphics-diagnostics.md) | Grafik Tanılama, DirectX oyunları ve uygulamalarında işleme hatalarında hata ayıklamanıza nasıl yardımcı olduğunu gösterir. |
