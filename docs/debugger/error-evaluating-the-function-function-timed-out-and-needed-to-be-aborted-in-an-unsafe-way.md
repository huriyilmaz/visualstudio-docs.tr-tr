---
title: İşlevin &apos; değerlendirilmesi zaman içinde zamanlandı ve işlevin güvenli olmayan bir şekilde &apos; iptal | Microsoft Docs
description: "Tam ileti metni: 'işlev' işlevinin değerlendirilmesi zaman doldu ve güvenli olmayan bir şekilde iptal edildi."
ms.date: 06/18/2021
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unsafe_func_eval_abort
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e928bb0ebae1e644729fcaf4f47b7dd461399be6
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386676"
---
# <a name="error-evaluating-the-function-39function39-timed-out-and-needed-to-be-aborted-in-an-unsafe-way"></a>Hata: İşlevin değerlendirme &#39;zaman&#39; ve güvenli olmayan bir şekilde iptal etmek gerekiyor

Tam ileti metni: 'işlev' işlevinin değerlendirilmesi zaman doldu ve güvenli olmayan bir şekilde iptal edildi. Bu, hedef işlemi bozmuş olabilir.

.NET nesnelerinin durumunu incelemeyi kolaylaştırmak için hata ayıklayıcı otomatik olarak hata ayıklama işlemini ek kod çalıştırmaya zorlar (genellikle özellik getter yöntemleri ve ToString işlevleri). Çoğu senaryoda bu işlevler hızla tamamlanır ve hata ayıklama çok daha kolay hale getirir. Ancak hata ayıklayıcısı uygulamayı korumalı alanda çalıştırmaz. Sonuç olarak, yanıt vermeyi durduran yerel bir işleve çağrılan bir özellik getter veya ToString yöntemi kurtarılmayabilirsiniz uzun zaman aşımlarına yol açabilirsiniz. Bu hata iletisiyle karşılaşırsanız bu oluştu.

Bu sorunun yaygın nedenlerinden biri, hata ayıklayıcısı bir özelliği değerlendirerek yalnızca inceleyen iş parçacığının yürütülmesinin gerekli olmasıdır. Bu nedenle özelliği hata ayıklamalı uygulamanın içinde diğer iş parçacıklarının çalışması için bekliyorsa ve .NET Çalışma Zamanı'nın kesintiye uğratmayacağı bir şekilde bekliyorsa bu sorun meydana gelir.

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

Bu sorunun çeşitli olası çözümleri için aşağıdaki bölümlere bakın.

## <a name="solution-1-prevent-the-debugger-from-calling-the-getter-property-or-tostring-method"></a>Çözüm #1: Hata ayıklayıcının getter özelliğini veya ToString yöntemini çağırması engellenebilir

Hata iletisi, hata ayıklayıcının çağırmaya çalıştığı işlevin adını size söyler. Bu işlevi değiştirebilirsiniz, hata ayıklayıcının özellik getter veya ToString yöntemini çağırması önlenebilir. Aşağıdakilerden birini deneyin:

* yöntemini özellik getter veya ToString yönteminin yanı sıra başka bir kod türüyle değiştirerek sorun gider.
  -veya-
* (ToString için) Türünde bir [DebuggerDisplay](../debugger/using-the-debuggerdisplay-attribute.md) özniteliği tanımlayın ve hata ayıklayıcının ToString dışında bir şeyi değerlendirmesine sahip olabilirsiniz.
  -veya-
* (Özellik alan için) [Özelliğine System.Diagnostics.DebuggerBrowsable(DebuggerBrowsableState.Never)](/dotnet/api/system.diagnostics.debuggerbrowsableattribute) özniteliğini koy. API uyumluluk nedenleriyle özelliğinin kalması gereken bir yönteminiz varsa, ancak gerçekten bir yöntem olması gerekirse bu yararlı olabilir.

## <a name="solution-2-have-the-target-code-ask-the-debugger-to-abort-the-evaluation"></a>Çözüm #2: Hedef kodun hata ayıklayıcıdan değerlendirmeyi durdurmasını istemesini iste

Hata iletisi, hata ayıklayıcının çağırmaya çalıştığı işlevin adını size söyler. Özellikle kodun kod çalıştırmak için başka bir iş parçacığına ihtiyacı olduğu durumlarda özellik getter veya ToString yöntemi bazen düzgün çalışmazsa, uygulama işlevi hata ayıklayıcıdan işlev değerlendirmesini durdurmasını istemek için [System.Diagnostics.Debugger.NotifyOfCrossThreadDependency'i](/dotnet/api/system.diagnostics.debugger.notifyofcrossthreaddependency) çağırabilir. Bu çözümle, bu işlevleri açıkça değerlendirmek hala mümkündür, ancak varsayılan davranış NotifyOfCrossThreadDependency çağrısı oluştuğunda yürütmenin durdurulmasıdır.

## <a name="solution-3-disable-all-implicit-evaluation"></a>Çözüm #3: Tüm örtülü değerlendirmeyi devre dışı bırakma

Önceki çözümler sorunu düzeltene kadar Araçlar Seçenekleri'ne gidin ve Hata Ayıklama Genel Etkinleştirme özelliği değerlendirmesi ve diğer örtülü işlev çağrıları ayarının  >     >    >  **işaretini kaldırın.** Bu, çoğu örtülü işlev değerlendirmesini devre dışı bırakarak sorunu çözecek.

## <a name="solution-4-check-compatibility-with-third-party-developer-tools"></a>Çözüm #4: Üçüncü taraf geliştirici araçlarıyla uyumluluğu denetleme

Resharper kullanıyorsanız öneriler için bu [soruna](https://youtrack.jetbrains.com/issue/RSRP-476824) bakın.

## <a name="solution-5-enable-managed-compatibility-mode"></a>Çözüm #5: Yönetilen uyumluluk modunu etkinleştirme

Eski hata ayıklama altyapısına geçiş yaptıysanız bu hatayı ortadan kaldırmış olabilirsiniz. Araçlar **Seçenekler'e**  >  gidin ve Hata Ayıklama Genel **Kullanım**  >  **yönetilen**  >  **uyumluluk modu ayarını seçin.** Daha fazla bilgi için [bkz. Genel hata ayıklama seçenekleri.](../debugger/general-debugging-options-dialog-box.md)
