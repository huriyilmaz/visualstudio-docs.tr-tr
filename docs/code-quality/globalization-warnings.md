---
title: Genelleştirme Uyarıları
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0ff17a56be7d7908ced0e37d1b13e8296ffc2c3d
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/31/2020
ms.locfileid: "89219692"
---
# <a name="globalization-warnings"></a>Genelleştirme Uyarıları
Genelleştirme Uyarıları, dünyaya yönelik kitaplıkları ve uygulamaları destekler.

## <a name="in-this-section"></a>Bu Bölümde

|Kural|Description|
|----------|-----------------|
|[CA1300: MessageBoxOptions belirt](../code-quality/ca1300.md)|Doğru olarak sağdan sola okuma düzeni kullanan kültürler için bir ileti kutusu görüntülemek için Show yöntemi MessageBoxOptions numaralandırma RightAlign ve RtlReading üyeleri geçirilmelidir.|
|[CA1301: Yinelenen hızlandırıcılardan kaçının](../code-quality/ca1301.md)|Giriş anahtarı, bir hızlandırıcı olarak da bilinir, ALT anahtarını kullanarak klavye giriş denetimini sağlar. Birden çok denetim yinelenen erişim anahtarlarına sahip olduğunda, erişim anahtarının davranışı iyi tanımlı değildir.|
|[CA1302: Yerel özel dizeleri doğrudan programın içine gömmeyin](../code-quality/ca1302.md)|System.Environment.SpecialFolder numaralandırma özel sistem klasörlerine başvuran üyeleri içerir. Bu klasörlerin konumları farklı işletim sistemleri üzerinde farklı değerlere sahip olabilir; kullanıcı konumları değiştirebilir ve konumlar yerelleştirilmiştir. Environment. GetFolderPath yöntemi Environment. SpecialFolder numaralandırması, yerelleştirilmiş ve o anda çalışmakta olan bilgisayar için uygun olan konumları döndürür.|
|[CA1303: Harfleri yerelleştirilmiş parametreler olarak göndermeyin](../code-quality/ca1303.md)|Dışarıdan görülebilen bir yöntem, bir dize sabit değerini bir .NET oluşturucusuna veya yöntemine parametre olarak geçirir ve bu dize yerelleştirilebilir olmalıdır.|
|[CA1304: CultureInfo belirt](../code-quality/ca1304.md)|Yöntem veya Oluşturucu System.Globalization.CultureInfo parametre kabul eden aşırı yüklenmiş üye arar ve yöntem veya oluşturucu CultureInfo parametresi aşırı yükleme çağıramaz. Bir CultureInfo veya System.IFormatProvider nesnesi sağlanamadığında, aşırı yüklü üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiyi vermeyebilir.|
|[CA1305: IFormatProvider belirt](../code-quality/ca1305.md)|Yöntem veya oluşturucu System.IFormatProvider parametresini kabul eden aşırı yüklü bir veya daha fazla üye arar ve yöntem veya oluşturucu IFormatProvider parametre yüklemesini çağırmaz. Bir System.Globalization.CultureInfo veya IFormatProvider nesnesi sağlanamadığında, aşırı yüklü üye tarafından sağlanan varsayılan değer, tüm yerel ayarlarda istediğiniz etkiyi vermeyebilir.|
|[CA1306: Veri türleri için yereli ayarlayın](../code-quality/ca1306.md)|Yerel ayarlar, veri için kültür-özel sunum öğelerini, örneğin para birimi sembolleri, sayısal değerler için biçimleri ve sıralama düzeni için kullanılan biçimlendirme gibi değerleri belirler. Bir DataTable veya DataSet oluşturduğunuzda, yerel ayarı açık olarak ayarlamanız gerekir.|
|[CA1307: açıklık için StringComparison belirtin](../code-quality/ca1307.md)|StringComparison parametresi ayarlanmamış bir yöntemi aşırı bir dize karşılaştırma işleminde kullanır.|
|[CA1308: Dizeleri büyük harfe normalleştirin](../code-quality/ca1308.md)|Dizeler büyük harfe normalleştirilmeli. Küçük bir karakter grubu küçük harfe dönüştürüldüğünde gidiş dönüş yapamaz.|
|[CA1309: Sıralı StringComparison kullanın](../code-quality/ca1309.md)|StringComparison parametresini Ordinal ya da OrdinalIgnoreCase'a ayarlayamayan dilbilimsel olmayan dize karşılaştırma işlemi. Açıkça StringComparison.Ordinal veya StringComparison.OrdinalIgnoreCase için parametre ayarıyla kodunuz genellikle hızlanır, daha doğru olur ve daha güvenilir hale gelir.|
|[CA1310: dize karşılaştırmayı doğruluk için belirtin](../code-quality/ca1310.md)|Dize karşılaştırma işlemi, StringComparison parametresi ayarlanmamış ve varsayılan olarak kültüre özgü dize karşılaştırmayı kullanan bir yöntem aşırı yüklemesi kullanır.|
|[CA2101: P/Invoke dize bağımsız değişkenleri için sıralama belirtin](../code-quality/ca2101.md)|Platform çağırma üyesi kısmen güvenilen çağıranlar için izin verir, bir dize parametresine sahiptir ve dizeyi açıkça sıralamaz. Bu, olası bir güvenlik açığına neden olabilir.|
