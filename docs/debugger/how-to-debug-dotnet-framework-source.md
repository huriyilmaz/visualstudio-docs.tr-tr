---
title: .NET Framework kaynakta hata ayıkla | Microsoft Docs
Description: .NET Framework kaynakta hata ayıklamayı öğrenin. Bunu yapılandırmanız ve hata ayıklama sembollerini indirmeniz gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.topic: how-to
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 13a575ec2e77f1b715ec5f17324a6933d8cf0805
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398629"
---
# <a name="how-to-debug-net-framework-source"></a>Nasıl yapılır: .NET Framework kaynağında hata ayıklama

.NET Framework kaynakta hata ayıklamak için şunları yapmanız gerekir:

- .NET Framework kaynağına adımlamayı etkinleştirin.

- Kod için hata ayıklama sembollerine erişin.

  Hata ayıklama sembollerini hemen indirmeyi seçebilir veya daha sonra indirilmek üzere seçenekleri ayarlayabilirsiniz. Sembolleri hemen indirmezseniz, uygulamanızda hata ayıklamayı başlattığınız bir dahaki sefer indirilir. Hata ayıklama sırasında, sembolleri indirmek ve yüklemek için **modülleri** veya **çağrı yığını** pencerelerini de kullanabilirsiniz.

### <a name="to-enable-stepping-into-net-framework-source"></a>.NET Framework kaynağa adımlamayı etkinleştirmek için

1. **Araçlar** (veya **hata ayıklama** **>)** altında  >  **hata ayıklama**  >  **genel**' i seçin **.NET Framework kaynak adımlamayı etkinleştir** seçeneğini belirleyin.

   - Yalnızca kendi kodum etkinleştirdiyseniz, bir uyarı iletişim kutusu size Yalnızca kendi kodum artık devre dışı bırakıldığını söyler. **Tamam**’ı seçin.

   - Yerel bir sembol önbelleği ayarlanmamışsa, bir uyarı iletişim kutusu size varsayılan bir sembol önbelleğinin ayarlandığını söyler. **Tamam**’ı seçin.

1. **Seçenekler** iletişim kutusunu kapatmak için **Tamam ' ı** seçin.

### <a name="to-set-or-change-symbol-source-locations-and-loading-behavior"></a>Sembol kaynak konumlarını ve yükleme davranışını ayarlamak veya değiştirmek için

1. **Araçlar** (veya **hata ayıklama**) altındaki **semboller** kategorisini seçin > **Seçenekler**  >  **hata** ayıklayın.

1. **Simgeler** sayfasında, **sembol dosyası (. pdb) konumları** altında, genel Microsoft sembol sunucularından simgelere erişmek için **Microsoft sembol sunucuları** ' nı seçin. Diğer sembol konumlarını eklemek ve yükleme sırasını değiştirmek için araç çubuğu düğmelerini seçin.

1. Yerel semboller önbelleğinizi değiştirmek için **Bu dizindeki önbellek sembolleri** altında farklı bir konuma düzenleyin veya tarayın.

1. Sembolleri hemen indirmek için **tüm sembolleri yükle**' yi seçin. Bu düğme yalnızca hata ayıklama sırasında kullanılabilir.

   Sembolleri şimdi indirmezseniz, hata ayıklamayı bir sonraki başlatmanızda indirilir.

1. **Seçenekler** iletişim kutusunu kapatmak için **Tamam ' ı** seçin.

### <a name="to-load-symbols-from-the-modules-or-call-stack-windows"></a>Modüller veya çağrı yığını pencerelerini sembolleri yüklemek için

1. Hata ayıklama sırasında, Windows modüllerini **Hata Ayıkla**  >    >   (veya **Ctrl + Alt + U** tuşlarına basın) veya Windows çağrı **yığını hata ayıkla**  >    >   (**Ctrl + Alt + C**) seçeneğini belirleyerek pencereyi açın.

1. Sembolleri yüklenmeyen bir modüle sağ tıklayın. **Modüller** penceresinde sembol yükleme durumu, **semboller durum** sütununda bulunur. **Çağrı yığını** penceresinde, durum **çerçeve durumu** sütununda, çerçeve ise gri renkte olur.

   - Makinenizdeki bir klasörden sembol dosyalarını bulmak ve yüklemek için menüden **sembolleri yükle** ' yi seçin.

   - Hata ayıklayıcının semboller için aradığı konumları göstermek için **sembol yükleme bilgileri** ' ni seçin.

   - **Semboller** sayfasını açmak Için **sembol ayarları** ' nı seçin. **Simgeler** sayfasında, **sembol dosyası (. pdb) konumları** altında, genel Microsoft sembol sunucularından simgelere erişmek için **Microsoft sembol sunucuları** ' nı seçin. Diğer sembol konumlarını eklemek ve yükleme sırasını değiştirmek için araç çubuğu düğmelerini seçin. İletişim kutusunu kapatmak için **Tamam ' ı** seçin.

### <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)
- [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)