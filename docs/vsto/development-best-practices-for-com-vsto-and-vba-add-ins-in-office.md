---
title: 'geliştirme için en iyi yöntemler: COM, VSTO, & VBA eklentileri Office'
description: Microsoft Office için COM, VSTO ve VBA eklentilerini geliştirirken önerilen en iyi yöntemler hakkında bilgi edinin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 523f339fb26ea12e8e737772a59002001d6302bb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106477"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Office 'de COM, VSTO ve VBA eklentileri için geliştirme için en iyi yöntemler
  Office için COM, VSTO veya VBA eklentileri geliştiriyorsanız, bu makalede açıklanan en iyi geliştirme uygulamalarını izleyin.   Bu, şunları sağlamanıza yardımcı olur:

- Farklı sürümlere ve Office dağıtımlarına yönelik eklentilerinizin uyumluluğu.
- Kullanıcılarınızın ve BT yöneticileriniz için eklenti dağıtımının azaldığı karmaşıklık.
- Yüklemenizin istenmeden yüklenmesi veya çalışma zamanı sorunları oluşmaz.

>not: Windows deposunun COM, VSTO veya VBA eklentisinin hazırlanması için [Masaüstü Köprüsü](/windows/uwp/porting/desktop-to-uwp-root) kullanmak desteklenmez. COM, VSTO ve VBA eklentileri Windows deposunda veya Office deposunda dağıtılamaz.

## <a name="do-not-check-for-office-during-installation"></a>yükleme sırasında Office denetleme
 eklentinin, eklenti yükleme işlemi sırasında Office yüklenip yüklenmediğini tespit etmemenizi önermiyoruz. Office yüklü değilse, eklentiyi yükleyebilirsiniz ve Office yüklendikten sonra kullanıcı bu erişime erişemez.

## <a name="use-embedded-interop-types-nopia"></a>Gömülü birlikte çalışma türlerini kullan (Nopıa)
çözümünüz .net 4,0 veya sonraki bir sürümü kullanıyorsa, Office birincil birlikte çalışma derlemelerine (pıa) yeniden dağıtılabilir olarak kullanmak yerine gömülü birlikte çalışma türleri (nopıa) kullanın. Tür ekleme kullanmak çözümünüzün yükleme boyutunu azaltır ve ileride uyumlulukla uyumluluk sağlar. Office 2010, pıa redistributable çalıştıran Office son sürümüdür. daha fazla bilgi için bkz. [izlenecek yol: Microsoft Office derlemelerinden tür bilgilerini katıştırma](/previous-versions/ee317478(v=vs.140)) ve [tür denklik ve katıştırılmış birlikte çalışma türleri](/windows/uwp/porting/desktop-to-uwp-root).

Çözümünüz .NET 'in önceki bir sürümünü kullanıyorsa, çözümünüzü .NET 4,0 veya üstünü kullanacak şekilde güncelleştirmenizi öneririz. .NET 4,0 veya sonraki bir sürümünü kullanmak Windows yeni sürümlerindeki çalışma zamanı önkoşullarını azaltır.

## <a name="avoid-depending-on-specific-office-versions"></a>belirli Office sürümlerine bağlı kalmamak için
çözümünüz yalnızca Office daha yeni sürümlerinde kullanılabilen işlevselliği kullanıyorsa, çalışma zamanında (örneğin, özel durum işleme veya sürümü denetleyerek) özelliğin var olduğunu (mümkünse özellik düzeyinde) doğrulayın. [Uygulama. Version özelliği](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>)gibi, nesne modelinde desteklenen API 'leri kullanarak, belirli sürümler yerine en düşük sürümleri doğrulayın. bunlar yüklemeler, ortamlar ve sürümler arasında değişebildiğinden, Office ikili meta verileri, yükleme yollarını veya kayıt defteri anahtarlarını kullanmanızı önermiyoruz.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>32-bit ve 64 bit Office kullanımını etkinleştir
Çözümünüz yalnızca belirli bir bit düzeyinde kullanılabilen kitaplıklara bağlı değilse, varsayılan derleme Hedefinizdeki her ikisi de 32-bit (x86) ve 64-bit (x64) ' i desteklemelidir. Office 'nin 64 bitlik sürümü, özellikle büyük veri ortamlarında benimseme sırasında artmaktadır. Hem 32 bit hem de 64 bit desteklemek, kullanıcılarınızın Office 32-bit ve 64 bit sürümleri arasında geçiş yapmayı kolaylaştırır.

VBA kodu yazarken, 64 bitlik güvenli bildirme deyimlerini kullanın ve değişkenleri uygun şekilde dönüştürün. ayrıca, her bir bit düzeyinde kod sağlayarak, belgelerin 32-bit veya 64-bit Office çalıştıran kullanıcılar arasında paylaşılabilmesi için de emin olun. daha fazla bilgi için bkz. [uygulamalara genel bakış için 64-bit Visual Basic](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Kısıtlı ortamları destekleme
Çözümünüz Kullanıcı hesabı yükseltmesi veya yönetici ayrıcalıkları gerektirmemelidir. Ayrıca, çözüm ayarlamaya veya değiştirmeye bağlı olmamalıdır:

- Geçerli çalışma dizini.
- DLL yükleme dizinleri.
- YOL değişkeni.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Paylaşılan verilerin ve ayarların kaydetme konumunu değiştirme
çözüm bir eklentinin ve Office dışında bir işlemden oluşuyorsa, eklenti ve dış işlem arasındaki verileri veya ayarları değiştirmek için kullanıcının uygulama verileri klasörünü veya kayıt defterini kullanmayın. Bunun yerine kullanıcının geçici klasörünü, Belgeler klasörünü veya çözümünüzün yükleme dizinini kullanmayı düşünün.

## <a name="increment-the-version-number-with-each-update"></a>Her güncelleştirme ile sürüm numarasını artırın
Çözümünüzde ikililerin sürüm numarasını ayarlayın ve her bir güncelleştirmeyle artırın. Bu, kullanıcıların sürümler ve uyumluluk değerlendirmesi arasındaki değişiklikleri belirlemesine daha kolay hale getirir.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Office en son sürümleri için destek deyimleri sağlayın
müşteriler, ısv 'ler için Office çalıştıran COM, VSTO ve VBA eklentileri için destek bildirimleri sağlamasını istiyor. açık destek deyimlerinizi listelemek, kurumsal hazırlık araçları için Microsoft 365 uygulamalar kullanan müşterilerin desteklerinizi anlamasına yardımcı olur.

Office istemci uygulamalarına yönelik destek deyimleri sağlamak için (örneğin, Word veya Excel), önce eklentilerinizin geçerli Office sürümünde çalıştırıldığını doğrulayın ve sonra eklenti daha sonraki bir sürümde kesintiye kesildiğinde güncelleştirmeler sağlamak için yürütün. Microsoft yeni bir yapı yayınlar veya Office bir güncelleştirme yayımlandığında eklentilerinizi test etmeniz gerekmez. Microsoft, Office COM, VSTO ve VBA genişletilebilirlik platformunu nadiren değiştirir ve bu değişiklikler iyi şekilde belgelenmiştir.

>Önemli: Microsoft, hazırlık raporları ve ISV iletişim bilgileri için desteklenen eklentilerin bir listesini tutar. Eklentiyi listeye almak için, bkz. [/ConfigMgr/Desktop-anallars/Ready-for-Windows](/configmgr/desktop-analytics/ready-for-windows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Yükleme veya yükleme sorunlarını ayıklamada yardımcı olması için Işlem Izleyicisini kullanın
Eklentilerinizin yükleme veya yükleme sırasında uyumluluk sorunları varsa, bu kişiler dosya veya kayıt defteri erişimiyle ilgili sorunlar ile ilişkili olabilir. Sorunu belirlemenize yardımcı olması için [Işlem izleyicisini](/sysinternals/downloads/procmon) veya benzer bir hata ayıklama aracını kullanarak bir çalışma ortamına karşı davranışı günlüğe kaydedin ve karşılaştırın.