---
title: Düzenle ve devam et ( C++görsel) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fef02f08ac635687eaaf071188ba0455c6389d9e
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301051"
---
# <a name="edit-and-continue-visual-c"></a>Düzenle ve Devam Et (Visual C++)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual C++ projelerinde Düzenle ve devam et ' i kullanabilirsiniz. Düzenle ve devam et sınırlamaları hakkında daha fazla bilgi için bkz. [desteklenen kod değişiklikleriC++()](../debugger/supported-code-changes-cpp.md) .  
  
 Visual Studio 2015 güncelleştirme 1 ' den itibaren, artık Windows Mağazası C++ uygulamaları ve DirectX uygulamalarında Düzenle ve devam et ' i kullanarak artık **/zı** derleyicisi anahtarıyla **/bigobj** anahtarını destekliyor. Ayrıca, **/fastlink** anahtarıyla derlenen Ikili dosyalarla Düzenle ve devam et ' i kullanabilirsiniz.  
  
 Diğer güncelleştirme 1 geliştirmeleri yeni, iptal edilebilen bir bekleme iletişim kutusu ve bir dosya Düzenle ve devam et desteği olmadığında bildirim içerir. Güncelleştirme 1 geliştirmeleri hakkında daha fazla bilgi için bkz. [Visual C++ Studio 2015 güncelleştirme 1 ' de Düzenle ve devam et geliştirmeleri](https://devblogs.microsoft.com/cppblog/improvements-for-c-edit-and-continue-in-visual-studio-2015-update-1/).  
  
 Visual Studio 2013 güncelleştirme 3 ' te tanıtılan [/Zo (En Iyi duruma getirilmiş hata ayıklama)](https://msdn.microsoft.com/library/eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f) derleyici seçeneği, [/OD (devre dışı bırak (Hata Ayıkla))](https://msdn.microsoft.com/library/aafb762y.aspx) seçeneği olmadan derlenen ikili dosyalar için. pdb (sembol) dosyalarına ek bilgi ekler.  
  
 **/Zo** düzenleme ve devam etmeyi devre dışı bırakır. Bkz. [nasıl yapılır: Iyileştirilmiş kodda hata ayıklama](../debugger/how-to-debug-optimized-code.md).  
  
## <a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a>Düzenle ve devam et 'i etkinleştir veya devre dışı bırak  
 Geçerli hata ayıklama oturumu sırasında uygulanmasını istemediğiniz kodda düzenleme yapıyorsanız otomatik Düzenle ve devam et çağrısını devre dışı bırakmak isteyebilirsiniz. Ayrıca otomatik düzenlemeyi yeniden etkinleştirip devam edebilirsiniz.  
  
1. **Araçlar** menüsünde **Seçenekler**' i seçin.  
  
2. **Seçenekler** iletişim kutusunda, **hata ayıklama/genel**' i seçin.  
  
3. **Düzenle ve devam et** grubunda **yerel düzenlemeyi etkinleştir ve devam et** onay kutusunu işaretleyin veya temizleyin.  
  
   Bu ayarın değiştirilmesi, üzerinde çalıştığınız tüm projeleri etkiler. Bu ayarı değiştirdikten sonra uygulamanızı yeniden oluşturmanız gerekmez. Hata ayıklarken bile ayarı değiştirebilirsiniz. Uygulamanızı komut satırından veya bir Makefile 'dan oluşturursanız, ancak Visual Studio ortamında hata ayıklaması yaparsanız, **/zı** seçeneğini ayarlarsanız Düzenle ve devam et ' i kullanmaya devam edebilirsiniz.  
  
## <a name="BKMK_How_to_apply_code_changes_explicitly"></a>Kod değişikliklerini açıkça uygulama  
 Visual C++'te Düzenle ve devam et, kod değişikliklerini iki şekilde uygulayabilir. Kod değişiklikleri, bir yürütme komutu seçtiğinizde ya da açıkça **kod değişikliklerini Uygula** komutu kullanılarak örtük bir şekilde uygulanabilir.  
  
 Kod değişikliklerini açıkça uyguladığınızda, programınız kesme modunda kalır; yürütme gerçekleşmez.  
  
- Kod değişikliklerini açıkça uygulamak için, **Hata Ayıkla** menüsünde, **kod değişikliklerini Uygula**' yı seçin.  
  
## <a name="BKMK_How_to_stop_code_changes"></a>Kod değişikliklerini durdurma  
 Düzenle ve devam et, kod değişikliklerini uygulama sürecinde olduğunda, işlemi durdurabilirsiniz.  
  
 Kod değişikliklerini uygulamayı durdurmak için:  
  
- **Hata Ayıkla** menüsünde, **kod değişikliklerini uygulamayı durdur**' u seçin.  
  
  Bu menü öğesi yalnızca kod değişiklikleri uygulanırken görülebilir.  
  
  Bu seçeneği belirlerseniz, kod değişikliklerinden hiçbiri yürütülmedi.  
  
## <a name="BKMK_How_to_reset_the_point_of_execution"></a>Yürütme noktasını sıfırlama  
 Bazı kod değişiklikleri, düzenleme ve devam etme değişiklikleri geçerliyse yürütme noktasının yeni bir konuma taşınmasına neden olabilir. Düzenle ve devam et, yürütme noktasını mümkün olduğunca doğru şekilde yerleştirirken, sonuçlar her durumda doğru olmayabilir.  
  
 Görselde C++, yürütme noktası değiştiğinde bir iletişim kutusu size bildirir. Hata ayıklamaya devam etmeden önce konumun doğru olduğunu doğrulamanız gerekir. Doğru değilse, **sonraki Ifadeyi ayarla** komutunu kullanın. Daha fazla bilgi için bkz. [çalıştırılacak sonraki Ifadeyi ayarlama](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).  
  
## <a name="BKMK_How_to_work_with_stale_code"></a>Eski kodla çalışma  
 Bazı durumlarda, Düzenle ve devam et kod değişikliklerini çalıştırılabilir dosyaya hemen uygulayamaz, ancak hata ayıklamaya devam ederseniz kod değişikliklerini uygulayabilir. Bu, geçerli işlevi çağıran bir işlevi düzenlediğinizde veya Çağrı yığınındaki bir işleve 64 bayttan fazla yeni değişken eklerseniz oluşur  
  
 Bu gibi durumlarda, değişiklikler uygulanana kadar hata ayıklayıcı orijinal kodu yürütmeye devam eder. Eski kod, `enc25.tmp`gibi bir başlık ile ayrı bir kaynak penceresinde geçici bir kaynak dosya penceresi olarak görünür. Düzenlenen kaynak özgün kaynak penceresinde görünmeye devam eder. Eski kodu düzenlemeye çalışırsanız bir uyarı iletisi görüntülenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Desteklenen Kod Değişiklikleri (C++)](../debugger/supported-code-changes-cpp.md)
