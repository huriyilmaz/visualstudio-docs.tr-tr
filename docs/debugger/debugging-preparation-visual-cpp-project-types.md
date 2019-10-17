---
title: Projelerde hata ayıklama C++ hazırlığı | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project templates, debugging
- C++ projects, debugging
- debug builds, project settings
- debugging [C++]
ms.assetid: 912b4ba2-7719-43d5-b087-db33e3f9329a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 9cf22bceedd026a641709640a6e29d1970000e3b
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72431417"
---
# <a name="debugging-preparation-c-project-types"></a>Hata ayıklama hazırlığı C++ : proje türleri
Bu bölümde, [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] proje şablonları tarafından oluşturulan temel proje türlerinde hata ayıklamanın nasıl yapılacağı açıklanmaktadır.

 Kendi çıktıları olarak DLL 'Ler oluşturan proje türlerinin, paylaştığı ortak özellikler nedeniyle [hata ayıklama dll projelerinde](../debugger/debugging-dll-projects.md) gruplandırıldığını unutmayın.

## <a name="BKMK_In_this_topic"></a>Bu konuda
 [Önerilen özellik ayarları](#BKMK_Recommended_Property_Settings)

 [Win32 projeleri](#BKMK_Win32_Projects)

- [C veya C++ Win32 uygulamasında hata ayıklamak için](#BKMK_To_debug_a_C_or_C___Win32_application)

- [Bir hata ayıklama yapılandırmasını el ile ayarlamak için](#BKMK_To_manually_set_a_Debug_configuration)

  [Windows Forms uygulamalar (.NET)](#BKMK_Windows_Forms_Applications___NET_)

## <a name="BKMK_Recommended_Property_Settings"></a>Önerilen özellik ayarları
 Bazı özellikler, tüm yönetilmeyen hata ayıklama senaryolarında aynı şekilde ayarlanmalıdır. Aşağıdaki tablolarda önerilen özellik ayarları görüntülenir. Burada listelenmeyen ayarlar, farklı yönetilmeyen proje türleri arasında farklılık gösterebilir. Daha fazla bilgi için bkz. [ C++ hata ayıklama yapılandırması için proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md).

### <a name="configuration-properties-124-cc-124-optimization-node"></a>Yapılandırma özellikleri &#124; C/C++ &#124; optimizasyon düğümü

|Özellik adı|Ayar|
|-------------------|-------------|
|**İyileştirme**|**Devre dışı olarak ayarla (/0d).** Üretilen yönergeler doğrudan kaynak kodunuza karşılık gelmediğinden, iyileştirilmiş kodun hata ayıklama işlemi daha zordur. Programınızın yalnızca en iyi duruma getirilmiş kodda görüntülenen bir hata olduğunu fark ederseniz, bu ayarı açabilirsiniz, ancak **ayrıştırma** penceresinde gösterilen kodun, kaynak pencerenize gördüklerinize uygun olmayan en iyi duruma getirilmiş kaynaktan oluşturulduğunu unutmayın. Adımlama gibi diğer özellikler beklendiği gibi davranmayabilir.|

### <a name="configuration-properties-124-linker-124-debugging-node"></a>Yapılandırma özellikleri &#124; bağlayıcı &#124; hata ayıklama düğümü

|Özellik adı|Ayar|
|-------------------|-------------|
|**Hata ayıklama bilgileri oluştur**|Hata ayıklama sembolleri ve hata ayıklama için gereken dosyaları oluşturmak için her zaman bu seçeneği **Evet (/Debug)** olarak ayarlamanız gerekir. Uygulama üretime geçtiğinde, onu kapalı olarak ayarlayabilirsiniz.|

 [Bu konuda](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Win32_Projects"></a>Win32 projeleri
 Win32 uygulamaları, C veya C++dilinde yazılmış geleneksel Windows programlarıdır. @No__t-0 ' da bu tür bir uygulama için hata ayıklama basittir.

 Win32 uygulamaları MFC uygulamalarını ve ATL projelerini içerir. Bunlar Windows API 'Lerini kullanır ve MFC veya ATL kullanabilir, ancak ortak dil çalışma zamanını (CLR) kullanmaz. Ancak, CLR kullanan yönetilen kodu çağırabilir.

 Aşağıdaki yordamda, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ' dan bir Win32 projesinde hata ayıklama işlemi açıklanmaktadır. Bir Win32 uygulamasında hata ayıklamanın başka bir yolu da uygulamayı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ' ın dışında başlatmanız ve buna iliştireklemektir. Daha fazla bilgi için bkz. [çalışan Işlemlere iliştirme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

### <a name="BKMK_To_debug_a_C_or_C___Win32_application"></a>C veya C++ Win32 uygulamasında hata ayıklamak için

1. Projeyi Visual Studio 'da açın.

2. **Hata Ayıkla** menüsünde **Başlat**' ı seçin.

3. Hata [ayıklayıcıyla ilk bakış](../debugger/debugger-feature-tour.md)bölümünde açıklanan teknikleri kullanarak hata ayıklayın.

### <a name="BKMK_To_manually_set_a_Debug_configuration"></a>Bir hata ayıklama yapılandırmasını el ile ayarlamak için

1. **Görünüm** menüsünde, **Özellik sayfaları**' na tıklayın.

2. Henüz yoksa açmak için **yapılandırma özellikleri** düğümüne tıklayın

3. **Genel**' i seçin ve **Çıkış** satırının değerini **Hata Ayıkla**olarak ayarlayın.

4. **C/C++**  düğümünü açın ve **genel**' i seçin.

    **Hata ayıklama** satırında, derleyici tarafından oluşturulacak hata ayıklama bilgilerinin türünü belirtirsiniz. **Program veritabanı (/Zi)** veya **Düzenle & devam et için program veritabanı (/Zi)** arasından seçim yapabilirsiniz.

5. **İyileştirme**' yi seçin ve **iyileştirme** satırında, açılır listeden **devre dışı (/0d)** seçeneğini belirleyin.

    Üretilen yönergeler doğrudan kaynak kodunuza karşılık gelmediğinden, iyileştirilmiş kodun hata ayıklama işlemi daha zordur. Programınızın yalnızca en iyi duruma getirilmiş kodda görüntülenen bir hata olduğunu fark ederseniz, bu ayarı açabilirsiniz, ancak ayrıştırma penceresinde gösterilen kodun, kaynak pencerenize gördüklerinize uygun olmayan en iyi duruma getirilmiş kaynaktan oluşturulduğunu unutmayın. Adımlama gibi özellikler büyük olasılıkla kesme noktaları ve yürütme noktası yanlış gösterilebilir.

6. **Bağlayıcı** düğümünü açın ve **hata ayıklama**öğesini seçin. İlk **Oluştur** satırında, açılan listeden **Evet (/Debug)** öğesini seçin. Hata ayıklama sırasında her zaman ayarlayın.

   Daha fazla bilgi için bkz.[ C++ hata ayıklama yapılandırması için proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md).

   [Bu konuda](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="BKMK_Windows_Forms_Applications___NET_"></a>Windows Forms uygulamalar (.NET)
 **Windows Forms Application (.net)** şablonu, bir [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] Windows Forms uygulaması oluşturur. Daha fazla bilgi için bkz. [nasıl yapılır: Windows uygulaması projesi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100)).

 @No__t-0 ' da bu tür bir uygulama hata ayıklaması, yönetilen Windows Forms uygulamalarında benzerdir.

 Proje şablonuyla bir Windows Forms projesi oluşturduğunuzda, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], hata ayıklama ve sürüm yapılandırması için gerekli ayarları otomatik olarak oluşturur. Gerekirse, bu ayarları **\<proje adı > Özellik sayfaları** iletişim kutusunda değiştirebilirsiniz. Daha fazla bilgi için bkz. [hata ayıklama ve yayın yapılandırması](../debugger/how-to-set-debug-and-release-configurations.md).

 Daha fazla bilgi için bkz. [ C++ hata ayıklama yapılandırması için proje ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md).

 Windows Forms bir uygulamada hata ayıklamanın bir diğer yolu da uygulamayı [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ' ın dışında başlatmak ve bu uygulamaya eklemektir. Daha fazla bilgi için bkz. [çalışan bir programa veya birden çok programa ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).

 [Bu konuda](../debugger/debugging-preparation-visual-cpp-project-types.md#BKMK_In_this_topic)

## <a name="see-also"></a>Ayrıca Bkz.
- [Hata ayıklayıcıya ilk bakış](../debugger/debugger-feature-tour.md)
- [C++ Hata Ayıklama Yapılandırması Proje Ayarları](../debugger/project-settings-for-a-cpp-debug-configuration.md)
- [Çalışan bir programa veya birden çok programa ekleme](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Hata ayıklama ve sürüm yapılandırması](../debugger/how-to-set-debug-and-release-configurations.md)
- [Nasıl yapılır: Windows uygulaması projesi oluşturma](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/42wc9kk5(v=vs.100))