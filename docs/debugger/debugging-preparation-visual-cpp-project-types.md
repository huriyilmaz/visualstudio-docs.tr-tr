---
title: C++ projelerinde hata ayıklamaya hazırlanma | Microsoft Docs
description: Visual C++ proje şablonları tarafından oluşturulan temel proje türlerinde hata ayıklamaya hazırlanma hakkında bilgi Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- cplusplus
ms.openlocfilehash: 461fbf9ca8518326c800baabbb4d67585895c7e9c23445d115dc6eb3c4f971c9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420333"
---
# <a name="debugging-preparation-c-project-types"></a>Hata Ayıklama Hazırlığı: C++ Project Türleri
Bu bölümde, proje şablonları tarafından oluşturulan temel proje türlerinde nasıl hata [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] ayıklayabilirsiniz?

 Çıkışları olarak DLL'ler oluşturan bu proje türlerinin, paylaştıları ortak özellikler nedeniyle Hata Ayıklama [DLL](../debugger/debugging-dll-projects.md) Projeleri'ne gruplandırıldıklarına dikkat alın.

## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Bu konu başlığında
 [Önerilen özellik ayarları](#BKMK_Recommended_Property_Settings)

 [Win32 projeleri](#BKMK_Win32_Projects)

- [C veya C++ Win32 uygulamasında hata ayıklamak için](#BKMK_To_debug_a_C_or_C___Win32_application)

- [Hata ayıklama yapılandırmasını el ile ayarlamak için](#BKMK_To_manually_set_a_Debug_configuration)

## <a name="recommended-property-settings"></a><a name="BKMK_Recommended_Property_Settings"></a> Önerilen özellik ayarları
 Bazı özellikler, tüm unmanaged hata ayıklama senaryolarında aynı şekilde ayarlayıcıdır. Aşağıdaki tablolarda önerilen özellik ayarları görüntülenir. Ayarlar listelenmiyorsa, farklı unmanaged proje türleri arasında değişiklik gösterebilir. Daha fazla bilgi için [bkz. Project Ayarlar C++ Hata Ayıklama Yapılandırması](../debugger/project-settings-for-a-cpp-debug-configuration.md)için yapılandırma.

### <a name="configuration-properties-124-cc-124-optimization-node"></a>C/C++ &#124; İyileştirme düğümü &#124; Yapılandırma Özellikleri

|Özellik Adı|Ayar|
|-------------------|-------------|
|**İyileştirme**|Devre Dışı **(/0d) olarak ayarlayın.** İyileştirilmiş kodun hata ayıklaması zordur çünkü oluşturulan yönergeler doğrudan kaynak kodunuzla ilgili değildir. Programda yalnızca iyileştirilmiş kodda görünen bir hata olduğunu bulursanız, bu ayarı açabilirsiniz, ancak **Disassembly** penceresinde gösterilen kodun kaynak pencerelerde gördüğünüzle eşleşmeyabilecek iyileştirilmiş kaynaktan oluşturula bir kod olduğunu unutmayın. Adımlama gibi diğer özellikler beklendiği gibi davranmay olabilir.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Bağlantı &#124; Hata Ayıklama &#124; Yapılandırma Özellikleri

|Özellik Adı|Ayar|
|-------------------|-------------|
|**Hata ayıklama bilgileri oluşturma**|Hata ayıklama için gereken hata ayıklama sembollerini ve dosyaları oluşturmak için bu seçeneği her zaman Evet **(/DEBUG)** olarak ayarlayabilirsiniz. Uygulama üretime geldiğinde kapalı olarak ayarlayın.|

 [Bu konu başlığında](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="win32-projects"></a><a name="BKMK_Win32_Projects"></a> Win32 projeleri
 Win32 uygulamaları, C Windows C++ ile yazılmış geleneksel uygulamalardır. içinde bu tür bir uygulamanın hata [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ayıklaması basittir.

 Win32 uygulamaları MFC uygulamalarını ve ATL projelerini içerir. Api'Windows kullanır ve MFC veya ATL kullanabilir, ancak ortak dil çalışma zamanı (CLR) kullanmaz. Ancak CLR kullanan yönetilen kodu çağırabilir.

 Aşağıdaki yordamda, içinde bir Win32 projesinin hata ayıklaması [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] açıkmektedir. Win32 uygulamasında hata ayıklamanın bir diğer yolu da uygulamayı dışında başlatmak [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ve uygulamaya eklemektir. Daha fazla bilgi için [bkz. Çalışan İşlemlere Ekleme.](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)

### <a name="to-debug-a-c-or-c-win32-application"></a><a name="BKMK_To_debug_a_C_or_C___Win32_application"></a> C veya C++ Win32 uygulamasında hata ayıklamak için

1. Projeyi Visual Studio'da açın.

2. Hata **Ayıkla menüsünde** Başlat'ı **seçin.**

3. Hata ayıklayıcısına ilk bakış konusunda [ele alınan teknikleri kullanarak hata ayıklama.](../debugger/debugger-feature-tour.md)

### <a name="to-manually-set-a-debug-configuration"></a><a name="BKMK_To_manually_set_a_Debug_configuration"></a> Hata ayıklama yapılandırmasını el ile ayarlamak için

1. Görünüm menüsünde **Özellik** **Sayfaları'nın üzerine tıklayın.**

2. Henüz **açılmamışsa** açmak için Yapılandırma Özellikleri düğümüne tıklayın

3. **Genel'i** seçin ve Çıkış satırı değerini **Hata Ayıkla** olarak **ayarlayın.**

4. **C/C++ düğümünü** açın ve Genel'i **seçin.**

    Hata **Ayıklama satırına** derleyici tarafından oluşturulan hata ayıklama bilgileri türünü belirtirsiniz. Program Veritabanı **(/Zi)** veya Düzenle için Program Veritabanı'nın Devam **(/ZI) & seçebilirsiniz.**

5. **İyileştirme'yi** seçin **ve İyileştirme** satırlarında, açılan listeden Devre Dışı **(/0d)** öğesini seçin.

    İyileştirilmiş kodun hata ayıklaması zordur çünkü oluşturulan yönergeler doğrudan kaynak kodunuzla ilgili değildir. Programda yalnızca iyileştirilmiş kodda görünen bir hata olduğunu bulursanız, bu ayarı açabilirsiniz, ancak Disassembly penceresinde gösterilen kodun kaynak pencerelerde gördüğünüzle eşleşmeyabilecek en iyi duruma getirilmiş kaynaktan oluşturulmuş olduğunu unutmayın. Adımlama gibi özellikler büyük olasılıkla kesme noktaları ve yürütme noktasını yanlış gösterir.

6. Linker **düğümünü açın** ve Hata **Ayıklama'ya tıklayın.** İlk Satır **oluştur'da,** açılan **listeden Evet (/DEBUG)** öğesini seçin. Hata ayıklarken bunu her zaman ayarlayın.

   Daha fazla bilgi için[bkz. Project Ayarlar C++ Hata Ayıklama Yapılandırması](../debugger/project-settings-for-a-cpp-debug-configuration.md)için yapılandırma.

   [Bu konu başlığında](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca bkz.
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [Project Ayarlar C++ Hata Ayıklama Yapılandırması için yapılandırma](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Çalışan Bir Programa veya Birden Çok Programa Ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Hata Ayıklama ve Sürüm Yapılandırmaları](../debugger/how-to-set-debug-and-release-configurations.md)