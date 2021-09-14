---
title: Yönetilen kod için Güvenlik Kuralları kural kümesi
ms.date: 11/04/2016
description: Eski kod analizi için Güvenlik Kuralları kural Visual Studio hakkında bilgi öğrenin. Olası güvenlik sorunlarına odaklanan kuralların açıklamalarına bakın.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 564aeac6-03fa-41b0-b655-88179f0ab01b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- dotnet
ms.openlocfilehash: 26aaec700d308e73249401e215fc1b1b93a87735
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631821"
---
# <a name="security-rules-rule-set-for-managed-code"></a>Yönetilen kod için Güvenlik Kuralları kural kümesi

Bildirilen olası güvenlik sorunlarının sayısını en üst düzeye çıkarmak için eski kod analizi için Microsoft Güvenlik Kuralları kural kümesi kullanın.

|Kural|Description|
|----------|-----------------|
|[CA2100](/dotnet/fundamentals/code-analysis/quality-rules/ca2100)|SQL sorgularını güvenlik açıkları için inceleyin|
|[CA2102](../code-quality/ca2102.md)|CLSCompliant olmayan özel durumları genel işleyiciler içinde yakalayın|
|[CA2103](../code-quality/ca2103.md)|Kesin temelli güvenliği gözden geçirin|
|[CA2104](../code-quality/ca2104.md)|Salt okunur kesilebilir başvuru türleri bildirmeyin|
|[CA2105](../code-quality/ca2105.md)|Dizi alanları salt okunur olmamalıdır|
|[CA2106](../code-quality/ca2106.md)|Onay deyimlerinin güvenliğini sağlayın|
|[CA2107](../code-quality/ca2107.md)|Gözden geçirmeyi reddedin ve yalnızca kullanımına izin verin|
|[CA2108](../code-quality/ca2108.md)|Değer türleri üzerinde bildirimsel güvenliği gözden geçirin|
|[CA2109](/dotnet/fundamentals/code-analysis/quality-rules/ca2109)|Görünen olay işleyicilerini gözden geçirin|
|[CA2111](../code-quality/ca2111.md)|İşaretçiler görünür olmamalıdır|
|[CA2112](../code-quality/ca2112.md)|Güvenli türler alanları açığa çıkarmamalıdır|
|[CA2114](../code-quality/ca2114.md)|Metot güvenliği türün bir üst kümesi olmalıdır|
|[CA2115](../code-quality/ca2115.md)|Yerel kaynaklar kullanırken GC.KeepAlive'ı çağırın|
|[CA2116](../code-quality/ca2116.md)|APTCA metotları yalnızca APTCA metotlarını çağırmalıdır|
|[CA2117](../code-quality/ca2117.md)|APTCA türleri yalnızca APTCA taban türlerini genişletmelidir|
|[CA2118](../code-quality/ca2118.md)|SuppressUnmanagedCodeSecurityAttribute kullanımını gözden geçirin|
|[CA2119](/dotnet/fundamentals/code-analysis/quality-rules/ca2119)|Özel arabirimleri karşılayan metotları mühürleyin|
|[CA2120](../code-quality/ca2120.md)|Serileştirme oluşturucularının güvenliğini sağlayın|
|[CA2121](../code-quality/ca2121.md)|Statik oluşturucular özel olmalıdır|
|[CA2122](../code-quality/ca2122.md)|Bağlantı talepleri olan metotları dolaylı olarak açığa çıkarmayın|
|[CA2123](../code-quality/ca2123.md)|Geçersiz kılan bağlantı talepleri taban ile özdeş olmalıdır|
|[CA2124](../code-quality/ca2124.md)|Savunmasız sonunda yan tümcelerini dış deneme içine sarmalayın|
|[CA2126](../code-quality/ca2126.md)|Tür bağlantı talepleri kalıtım taleplerini gerektirir|
|[CA2130](../code-quality/ca2130.md)|Güvenlik kritik sabitleri saydam olmalıdır|
|[CA2131](../code-quality/ca2131.md)|Güvenlik kritik türleri tür eşdeğerliğine katılamaz|
|[CA2132](../code-quality/ca2132.md)|Varsayılan oluşturucular en az taban tür varsayılan oluşturucular kadar kritik olmalıdır|
|[CA2133](../code-quality/ca2133.md)|Temsilciler tutarlı saydamlığı olan metotlara bağlanmalıdır|
|[CA2134](../code-quality/ca2134.md)|Metotlar taban metotları geçersiz kılarken tutarlı saydamlığı tutmalıdır|
|[CA2135](../code-quality/ca2135.md)|Düzey 2 derlemeler LinkDemands içermemelidir|
|[CA2136](../code-quality/ca2136.md)|Üyeler çakışan saydamlık ek açıklamalarına sahip olmamalıdır|
|[CA2137](../code-quality/ca2137.md)|Saydam metotlar yalnızca doğrulanabilir IL içermelidir|
|[CA2138](../code-quality/ca2138.md)|Saydam metotlar SuppressUnmanagedCodeSecurity özniteliğine sahip metotları çağırmamalıdır|
|[CA2139](../code-quality/ca2139.md)|Saydam metotlar HandleProcessCorruptingExceptions özniteliğini kullanamaz|
|[CA2140](../code-quality/ca2140.md)|Saydam kod güvenlik kritik nesnelerine başvurmamalıdır|
|[CA2141](../code-quality/ca2141.md)|Saydam yöntemler LinkDemands'ı karşılamamalı|
|[CA2142](../code-quality/ca2142.md)|Saydam kod LinkDemands ile korunmamalıdır|
|[CA2143](../code-quality/ca2143.md)|Saydam metotlar güvenlik taleplerini kullanmamalıdır|
|[CA2144](../code-quality/ca2144.md)|Saydam kod derlemeleri bayt dizilerinden yüklememelidir|
|[CA2145](../code-quality/ca2145.md)|Saydam metotlar SuppressUnmanagedCodeSecurityAttribute ile donatılmamalıdır|
|[CA2146](../code-quality/ca2146.md)|Türler en az kendi taban türleri ve arabirimleri kadar kritik olmalıdır|
|[CA2147](../code-quality/ca2147.md)|Saydam metotlar güvenlik onay deyimlerini kullanmamalıdır|
|[CA2149](../code-quality/ca2149.md)|Saydam metotlar yerel kod içine çağırmamalıdır|
|[CA2210](../code-quality/ca2210.md)|Derlemelerin geçerli tanımlayıcı adları olmalıdır|
|[CA2300](/dotnet/fundamentals/code-analysis/quality-rules/ca2300)|Güvenli olmayan seri durumdan çıkarıcı BinaryFormatter kullanmayın|
|[CA2301](/dotnet/fundamentals/code-analysis/quality-rules/ca2301)|İlk olarak BinaryFormatter.Binder öğesini ayarlamadan önce BinaryFormatter.Deserialize çağırmayın|
|[CA2302](/dotnet/fundamentals/code-analysis/quality-rules/ca2302)|BinaryFormatter.Deserialize çağırmadan önce BinaryFormatter.Binder öğesinin ayarlandığından emin olun|
|[CA2305](/dotnet/fundamentals/code-analysis/quality-rules/ca2305)|Güvenli olmayan seri kaldırıcı LosFormatter kullanmayın|
|[CA2310](/dotnet/fundamentals/code-analysis/quality-rules/ca2310)|Güvenli olmayan seri kaldırıcı NetDataContractSerializer kullanmayın|
|[CA2311](/dotnet/fundamentals/code-analysis/quality-rules/ca2311)|İlk olarak NetDataContractSerializer.Binder öğesini ayarlamadan seri durumdan çıkarmayın|
|[CA2312](/dotnet/fundamentals/code-analysis/quality-rules/ca2312)|Seri durumdan çıkarmadan önce NetDataContractSerializer.Binder öğesinin ayarlandığından emin olun|
|[CA2315](/dotnet/fundamentals/code-analysis/quality-rules/ca2315)|Güvenli olmayan seri kaldırıcı ObjectStateFormatter kullanmayın|
|[CA2321](/dotnet/fundamentals/code-analysis/quality-rules/ca2321)|SimpleTypeResolver kullanarak JavaScriptSerializer ile seri durumdan çıkarmayın|
|[CA2322](/dotnet/fundamentals/code-analysis/quality-rules/ca2322)|Seri durumdan çıkarmadan önce SimpleTypeResolver ile JavaScriptSerializer’ın başlatılmadığından emin olun|
|[CA3001](/dotnet/fundamentals/code-analysis/quality-rules/ca3001)|SQL ekleme güvenlik açıkları için inceleme kodu|
|[CA3002](/dotnet/fundamentals/code-analysis/quality-rules/ca3002)|XSS güvenlik açıkları için inceleme kodu|
|[CA3003](/dotnet/fundamentals/code-analysis/quality-rules/ca3003)|Dosya yolu ekleme güvenlik açıkları için inceleme kodu|
|[CA3004](/dotnet/fundamentals/code-analysis/quality-rules/ca3004)|Bilgilerin açığa çıkmasıyla ilgili güvenlik açıkları için inceleme kodu|
|[CA3005](/dotnet/fundamentals/code-analysis/quality-rules/ca3005)|LDAP ekleme güvenlik açıkları için inceleme kodu|
|[CA3006](/dotnet/fundamentals/code-analysis/quality-rules/ca3006)|İşlem komutu ekleme güvenlik açıkları için inceleme kodu|
|[CA3007](/dotnet/fundamentals/code-analysis/quality-rules/ca3007)|Açık yeniden yönlendirme güvenlik açıkları için inceleme kodu|
|[CA3008](/dotnet/fundamentals/code-analysis/quality-rules/ca3008)|XPath ekleme güvenlik açıkları için inceleme kodu|
|[CA3009](/dotnet/fundamentals/code-analysis/quality-rules/ca3009)|XML ekleme güvenlik açıkları için inceleme kodu|
|[CA3010](/dotnet/fundamentals/code-analysis/quality-rules/ca3010)|XAML ekleme güvenlik açıkları için inceleme kodu|
|[CA3011](/dotnet/fundamentals/code-analysis/quality-rules/ca3011)|DLL ekleme güvenlik açıkları için inceleme kodu|
|[CA3012](/dotnet/fundamentals/code-analysis/quality-rules/ca3012)|Normal ifade ekleme güvenlik açıkları için inceleme kodu|
|[CA5358](/dotnet/fundamentals/code-analysis/quality-rules/ca5358)|Güvenli Olmayan Şifreleme Modlarını Kullanmayın|
|[CA5403](/dotnet/fundamentals/code-analysis/quality-rules/ca5403)|Sertifikayı sabit olarak kodlamayın|