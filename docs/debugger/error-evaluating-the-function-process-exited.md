---
title: Hata-hedef işlemden &#39;işlev &#39;işlevi değerlendirilirken&#39; kodla çıkış yaptı&#39; | Microsoft Docs
ms.date: 4/06/2018
ms.topic: error-reference
f1_keywords:
- vs.debug.error.process_exit_during_func_eval
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d1721196becf1f746d81fa7e3d4ff5f0371e3f57
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/27/2020
ms.locfileid: "85460784"
---
# <a name="error-the-target-process-exited-with-code-39code39-while-evaluating-the-function-39function39"></a>Hata: işlev &#39;işlevi değerlendirilirken hedef işleme kod &#39;kodla çıkıldı&#39;&#39;

Tam ileti metni: ' function ' işlevi değerlendirilirken hedef işlemden ' Code ' kodu ile çıkıldı.

.NET nesnelerinin durumunu incelemeyi kolaylaştırmak için, hata ayıklama işlemini ek kod (genellikle özellik alıcı yöntemleri ve işlevleri) çalıştırmaya otomatik olarak zorlar `ToString` . Çoğu senaryoda, bu işlevler başarıyla tamamlanır veya hata ayıklayıcı tarafından yakalanarak özel durumlar oluşturur. Ancak, çekirdek sınırları üzerinde yer aldığı, kullanıcı iletisi pompalama gerektirdiğinden veya kurtarılamaz olduğundan özel durumların yakalanamadığı bazı durumlar vardır. Sonuç olarak, işlemi açıkça sonlandıran kodu yürüten bir özellik alıcı veya ToString yöntemi (örneğin, çağrılar `ExitProcess()` ) veya yakalanamayan bir işlenmeyen özel durum oluşturur (örneğin, `StackOverflowException` ), hata ayıklanan işlemi sonlandırır ve hata ayıklama oturumunu sonlandırır. Bu hata iletisiyle karşılaşırsanız, bu oluştu.

Bu sorunun yaygın bir nedeni, hata ayıklayıcı kendisini çağıran bir özelliği değerlendirirken, yığın taşması özel durumuna neden olabilir. Yığın taşması özel durumu kurtarılamıyor ve hedef işlem sonlandırılacak.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

Bu sorunun iki olası çözümü vardır.

### <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Çözüm #1: hata ayıklayıcının alıcı özelliğini veya ToString metodunu aramasını engelleyin 

Hata mesajı, hata ayıklayıcının çağrı gerçekleştirmeye çalıştığı işlevin adını bildirir. İşlevin adı ile, değerlendirmede hata ayıklamak için bu işlevi **komut** penceresinden yeniden değerlendirmeyi deneyebilirsiniz. Doğrudan **pencereden değerlendirilirken** hata ayıklama yapılabilir çünkü, **oto s/Yereller/izleme** pencerelerinde örtük değerlendirmelere benzediğinde, hata ayıklayıcı işlenmemiş özel durumlara karşı kesilir.

Bu işlevi değiştirebiliyorsanız, hata ayıklayıcının özellik alıcı veya yöntemini aramasını engelleyebilirsiniz `ToString` . Aşağıdakilerden birini deneyin:

* Yöntemi bir özellik alıcı veya ToString yönteminin yanı sıra diğer kod türlerine de değiştirin ve sorun devam eder.
    -veya-
* (İçin `ToString` ) Türünde bir `DebuggerDisplay` öznitelik tanımlayın ve hata ayıklayıcının dışında bir şeyi değerlendirebilmeniz gerekir `ToString` .
    -veya-
* (Bir özellik alıcısı için) `[System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)]`Özniteliği özelliğine yerleştirin. Bu, API uyumluluğu nedenleriyle bir özelliğin kalması gereken bir yönteminiz varsa, ancak gerçekten bir yöntem olması halinde yararlı olabilir.

Bu yöntemi değiştiremeyeceğiniz takdirde, bir alternatif yönergede hedef işlemi bölebilir ve değerlendirmeyi yeniden deneyebilirsiniz.

### <a name="solution-2-disable-all-implicit-evaluation"></a>Çözüm #2: tüm örtük değerlendirmeyi devre dışı bırak

Önceki çözümler sorunu gidermezse, **Araçlar**  >  **Seçenekler**' e gidin ve **hata ayıklama**  >  **genel**  >  **etkinleştirme özelliği değerlendirmesi ve diğer örtük işlev çağrıları**seçeneğinin işaretini kaldırın. Bu, çoğu örtük işlev değerlendirmesini devre dışı bırakır ve sorunu çözmelidir.
