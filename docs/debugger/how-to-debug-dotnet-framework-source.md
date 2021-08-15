---
title: .NET Framework kaynakta hata ayıkla | Microsoft Docs
description: .NET Framework kaynakta hata ayıklamayı öğrenin. Bunu yapılandırmanız ve hata ayıklama sembollerini indirmeniz gerekir.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.topic: how-to
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- dotnet
ms.openlocfilehash: ee02da8dac8ffdd2f6900f6530f39e256448fafd9d6229a0946034d39ed3dca1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453825"
---
# <a name="how-to-debug-net-framework-source"></a>nasıl yapılır: .NET Framework kaynağında hata ayıklama

.NET Framework kaynakta hata ayıklamak için şunları yapmanız gerekir:

- .NET Framework kaynağına adımlamayı etkinleştirin.

- Kod için hata ayıklama sembollerine erişin.

  Hata ayıklama sembollerini hemen indirmeyi seçebilir veya daha sonra indirilmek üzere seçenekleri ayarlayabilirsiniz. Sembolleri hemen indirmezseniz, uygulamanızda hata ayıklamayı başlattığınız bir dahaki sefer indirilir. Hata ayıklama sırasında, sembolleri indirmek ve yüklemek için **modülleri** veya **çağrı yığını** pencerelerini de kullanabilirsiniz.

### <a name="to-enable-stepping-into-net-framework-source"></a>.NET Framework kaynağa adımlamayı etkinleştirmek için

1. **araçlar** (veya **hata ayıklama** **>)** altında  >  **hata ayıklama**  >  **genel**' i seçin **.NET Framework kaynak adımlamayı etkinleştir** seçeneğini belirleyin.

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

1. hata ayıklama sırasında **, hata ayıklama** Windows modüller ' i seçerek pencereyi açın  >    >   (veya **ctrl + alt + U** tuşlarına basın) veya   >  **Windows**  >  **çağrı yığınında** hata ayıklayın (**ctrl + alt + C**).

1. Sembolleri yüklenmeyen bir modüle sağ tıklayın. **Modüller** penceresinde sembol yükleme durumu, **semboller durum** sütununda bulunur. **Çağrı yığını** penceresinde, durum **çerçeve durumu** sütununda, çerçeve ise gri renkte olur.

   - Makinenizdeki bir klasörden sembol dosyalarını bulmak ve yüklemek için menüden **sembolleri yükle** ' yi seçin.

   - Hata ayıklayıcının semboller için aradığı konumları göstermek için **sembol yükleme bilgileri** ' ni seçin.

   - **semboller** sayfasını açmak için **sembol Ayarlar** seçin. **Simgeler** sayfasında, **sembol dosyası (. pdb) konumları** altında, genel Microsoft sembol sunucularından simgelere erişmek için **Microsoft sembol sunucuları** ' nı seçin. Diğer sembol konumlarını eklemek ve yükleme sırasını değiştirmek için araç çubuğu düğmelerini seçin. İletişim kutusunu kapatmak için **Tamam ' ı** seçin.

### <a name="see-also"></a>Ayrıca bkz.
- [Yönetilen kodda hata ayıklama](../debugger/debugging-managed-code.md)
- [Sembol (. pdb) ve kaynak dosyaları belirtme](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
