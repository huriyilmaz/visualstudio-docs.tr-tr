---
title: Düzenle ve devam et (C++) | Microsoft Docs
ms.date: 05/31/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Edit and Continue [C++]
- debugging [C++], Edit and Continue
- C/C++, Edit and Continue
ms.assetid: 1815251e-a877-433e-9e5e-69bd9ba254c7
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: c2d92477e37b4918e0601bf163e07f5a8492136c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72737908"
---
# <a name="edit-and-continue-c"></a>Düzenle ve Devam Et (C++)
C++ projelerinde Düzenle ve devam et ' i kullanabilirsiniz. Düzenle ve devam et sınırlamaları hakkında daha fazla bilgi için bkz. [desteklenen kod değişiklikleri (C++)](../debugger/supported-code-changes-cpp.md) .

Visual Studio 2015 güncelleştirme 3 geliştirmeleri hakkında daha fazla bilgi için bkz. [Visual studio 2015 güncelleştirme 3 ' te C++ Düzenle ve devam et](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

 Visual Studio 2013 güncelleştirme 3 ' te tanıtılan [/Zo (En Iyi duruma getirilmiş hata ayıklama)](/cpp/build/reference/zo-enhance-optimized-debugging) derleyici seçeneği, [/OD (devre dışı bırak (Hata Ayıkla))](https://msdn.microsoft.com/library/aafb762y.aspx) seçeneği olmadan derlenen ikili dosyalar için. pdb (sembol) dosyalarına ek bilgi ekler.

 **/Zo** düzenleme ve devam etmeyi devre dışı bırakır. Bkz. [nasıl yapılır: Iyileştirilmiş kodda hata ayıklama](../debugger/how-to-debug-optimized-code.md).

## <a name="enable-or-disable-edit-and-continue"></a><a name="BKMK_Enable_or_disable_automatic_invocation_of_Edit_and_Continue"></a> Düzenle ve devam et 'i etkinleştir veya devre dışı bırak
 Geçerli hata ayıklama oturumu sırasında uygulanmasını istemediğiniz kodda düzenleme yapıyorsanız otomatik Düzenle ve devam et çağrısını devre dışı bırakmak isteyebilirsiniz. Ayrıca otomatik düzenlemeyi yeniden etkinleştirip devam edebilirsiniz.

> [!IMPORTANT]
> Gerekli derleme ayarları ve özellik uyumluluğu hakkında diğer bilgiler için bkz. [Visual Studio 2015 güncelleştirme 3 ' te C++ Düzenle ve devam et](https://devblogs.microsoft.com/cppblog/c-edit-and-continue-in-visual-studio-2015-update-3/).

1. Hata ayıklama oturumundaysanız, hata ayıklamayı durdurun (**SHIFT + F5**).

2. **Araçlar** menüsünde **Seçenekler**' i seçin.

3. **Seçenekler** iletişim kutusunda, **hata ayıklama > genel**' i seçin.

4. Etkinleştirmek için **Düzenle ve devam et 'ı etkinleştir**' i seçin. Devre dışı bırakmak için onay kutusunu temizleyin.

5. **Düzenle ve devam et** grubunda **yerel düzenlemeyi etkinleştir ve devam et** onay kutusunu işaretleyin veya temizleyin.

   Bu ayarın değiştirilmesi, üzerinde çalıştığınız tüm projeleri etkiler. Bu ayarı değiştirdikten sonra uygulamanızı yeniden oluşturmanız gerekmez. Uygulamanızı komut satırından veya bir Makefile 'dan oluşturursanız, ancak Visual Studio ortamında hata ayıklaması yaparsanız, **/zı** seçeneğini ayarlarsanız Düzenle ve devam et ' i kullanmaya devam edebilirsiniz.

## <a name="how-to-apply-code-changes-explicitly"></a><a name="BKMK_How_to_apply_code_changes_explicitly"></a> Kod değişikliklerini açıkça uygulama
 C++ ' da Düzenle ve devam et, kod değişikliklerini iki şekilde uygulayabilir. Kod değişiklikleri, bir yürütme komutu seçtiğinizde ya da açıkça **kod değişikliklerini Uygula** komutu kullanılarak örtük bir şekilde uygulanabilir.

 Kod değişikliklerini açıkça uyguladığınızda, programınız kesme modunda kalır; yürütme gerçekleşmez.

- Kod değişikliklerini açıkça uygulamak için, **Hata Ayıkla** menüsünde, **kod değişikliklerini Uygula**' yı seçin.

## <a name="how-to-stop-code-changes"></a><a name="BKMK_How_to_stop_code_changes"></a> Kod değişikliklerini durdurma
 Düzenle ve devam et, kod değişikliklerini uygulama sürecinde olduğunda, işlemi durdurabilirsiniz.

 Kod değişikliklerini uygulamayı durdurmak için:

- **Hata Ayıkla** menüsünde, **kod değişikliklerini uygulamayı durdur**' u seçin.

  Bu menü öğesi yalnızca kod değişiklikleri uygulanırken görülebilir.

  Bu seçeneği belirlerseniz, kod değişikliklerinden hiçbiri yürütülmedi.

## <a name="how-to-reset-the-point-of-execution"></a><a name="BKMK_How_to_reset_the_point_of_execution"></a> Yürütme noktasını sıfırlama
 Bazı kod değişiklikleri, düzenleme ve devam etme değişiklikleri geçerliyse yürütme noktasının yeni bir konuma taşınmasına neden olabilir. Düzenle ve devam et, yürütme noktasını mümkün olduğunca doğru şekilde yerleştirirken, sonuçlar her durumda doğru olmayabilir.

 C++ ' da, yürütme noktası değiştiğinde bir iletişim kutusu size bildirir. Hata ayıklamaya devam etmeden önce konumun doğru olduğunu doğrulamanız gerekir. Doğru değilse, **sonraki Ifadeyi ayarla** komutunu kullanın. Daha fazla bilgi için bkz. [çalıştırılacak sonraki Ifadeyi ayarlama](https://msdn.microsoft.com/library/y740d9d3.aspx#BKMK_Set_the_next_statement_to_execute).

## <a name="how-to-work-with-stale-code"></a><a name="BKMK_How_to_work_with_stale_code"></a> Eski kodla çalışma
 Bazı durumlarda, Düzenle ve devam et kod değişikliklerini çalıştırılabilir dosyaya hemen uygulayamaz, ancak hata ayıklamaya devam ederseniz kod değişikliklerini uygulayabilir. Bu, geçerli işlevi çağıran bir işlevi düzenlediğinizde veya Çağrı yığınındaki bir işleve 64 bayttan fazla yeni değişken eklerseniz oluşur

 Bu gibi durumlarda, değişiklikler uygulanana kadar hata ayıklayıcı orijinal kodu yürütmeye devam eder. Eski kod, farklı bir kaynak penceresinde, gibi bir başlık ile geçici bir kaynak dosya penceresi olarak görünür `enc25.tmp` . Düzenlenen kaynak özgün kaynak penceresinde görünmeye devam eder. Eski kodu düzenlemeye çalışırsanız bir uyarı iletisi görüntülenir.

## <a name="see-also"></a>Ayrıca bkz.
- [Desteklenen kod değişiklikleri (C++)](../debugger/supported-code-changes-cpp.md)