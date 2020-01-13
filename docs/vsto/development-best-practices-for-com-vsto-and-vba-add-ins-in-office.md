---
title: "Geliştirme için en iyi Yöntemler: Office 'te COM, VSTO, & VBA eklentileri"
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 716345cd2df3e941ea3d50cfc1519dc86dcd7077
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918636"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Office 'te COM, VSTO ve VBA eklentileri için geliştirme için en iyi yöntemler
  Office için COM, VSTO veya VBA eklentileri geliştiriyorsanız, bu makalede açıklanan en iyi geliştirme uygulamalarını izleyin.   Bu, şunları sağlamanıza yardımcı olur:

- Office 'in farklı sürümlerinde ve dağıtımlarındaki eklentilerin uyumluluğu.
- Kullanıcılarınızın ve BT yöneticileriniz için eklenti dağıtımının azaldığı karmaşıklık.
- Yüklemenizin istenmeden yüklenmesi veya çalışma zamanı sorunları oluşmaz.

>Not: Windows Mağazası için COM, VSTO veya VBA eklentisinin hazırlanması için [Masaüstü Köprüsü](/windows/uwp/porting/desktop-to-uwp-root) 'nün kullanılması desteklenmez. COM, VSTO ve VBA eklentileri Windows Mağazası 'nda veya Office Mağazası 'nda dağıtılamaz.

## <a name="do-not-check-for-office-during-installation"></a>Yükleme sırasında Office 'i denetleme
 Eklentinin, eklenti yükleme işlemi sırasında Office 'in yüklü olup olmadığını algılamasını önermeyiz. Office yüklü değilse, eklentiyi yükleyebilirsiniz ve Office yüklendikten sonra Kullanıcı bu eklentiye erişebilir.

## <a name="use-embedded-interop-types-nopia"></a>Gömülü birlikte çalışma türlerini kullan (Nopıa)
Çözümünüz .NET 4,0 veya sonraki bir sürümü kullanıyorsa, Office birincil birlikte çalışma derlemeleri (PIA) yeniden dağıtılabilir öğesine göre değil, gömülü birlikte çalışma türleri (Nopıa) kullanın. Tür ekleme kullanmak çözümünüzün yükleme boyutunu azaltır ve ileride uyumlulukla uyumluluk sağlar. Office 2010, PIA Redistributable çalıştıran Office 'in son sürümüdür. Daha fazla bilgi için bkz. [Izlenecek yol: Microsoft Office Derlemelerinden tür bilgilerini katıştırma](https://msdn.microsoft.com/library/ee317478.aspx) ve [tür denklik ve katıştırılmış birlikte çalışma türleri](/windows/uwp/porting/desktop-to-uwp-root).

Çözümünüz .NET 'in önceki bir sürümünü kullanıyorsa, çözümünüzü .NET 4,0 veya üstünü kullanacak şekilde güncelleştirmenizi öneririz. .NET 4,0 veya sonraki bir sürümünü kullanmak, Windows 'un daha yeni sürümlerindeki çalışma zamanı önkoşullarını azaltır.

## <a name="avoid-depending-on-specific-office-versions"></a>Belirli Office sürümlerine bağlı kalmamak için
Çözümünüz yalnızca Office 'in daha yeni sürümlerinde kullanılabilen işlevselliği kullanıyorsa, çalışma zamanında (örneğin, özel durum işleme veya sürümü denetleyerek) özelliğin var olduğunu (mümkünse özellik düzeyinde) doğrulayın. [Uygulama. Version özelliği](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>)gibi, nesne modelinde desteklenen API 'leri kullanarak, belirli sürümler yerine en düşük sürümleri doğrulayın. Office ikili meta verileri, yükleme yolları veya kayıt defteri anahtarlarına güvenmenizi öneririz, çünkü bunlar Yüklemeler, ortamlar ve sürümler arasında değişebilir.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>32-bit ve 64 bit Office kullanımını etkinleştir
Çözümünüz yalnızca belirli bir bit düzeyinde kullanılabilen kitaplıklara bağlı değilse, varsayılan derleme Hedefinizdeki her ikisi de 32-bit (x86) ve 64-bit (x64) ' i desteklemelidir. Office 'in 64 bitlik sürümü, özellikle büyük veri ortamlarında benimseme aşamasında artmaktadır. Hem 32 bit hem de 64 bit desteklemek, kullanıcılarınızın Office 'in 32-bit ve 64 bit sürümleri arasında geçiş yapmayı kolaylaştırır.

VBA kodu yazarken, 64 bitlik güvenli bildirme deyimlerini kullanın ve değişkenleri uygun şekilde dönüştürün. Ayrıca, her bir bit düzeyinde kod sağlayarak Office 'in 32-bit veya 64-bit sürümlerini çalıştıran kullanıcılar arasında belgelerin paylaşılabilmesi için de emin olun. Daha fazla bilgi için bkz. [uygulamalara genel bakış için 64-bit Visual Basic](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Kısıtlı ortamları destekleme
Çözümünüz Kullanıcı hesabı yükseltmesi veya yönetici ayrıcalıkları gerektirmemelidir. Ayrıca, çözüm ayarlamaya veya değiştirmeye bağlı olmamalıdır:

- Geçerli çalışma dizini.
- DLL yükleme dizinleri.
- YOL değişkeni.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Paylaşılan verilerin ve ayarların kaydetme konumunu değiştirme
Çözüm bir eklentinin ve Office dışındaki bir işlemden oluşuyorsa, eklenti ve dış işlem arasındaki verileri veya ayarları değiştirmek için kullanıcının uygulama verileri klasörünü veya kayıt defterini kullanmayın. Bunun yerine kullanıcının geçici klasörünü, Belgeler klasörünü veya çözümünüzün yükleme dizinini kullanmayı düşünün.

## <a name="increment-the-version-number-with-each-update"></a>Her güncelleştirme ile sürüm numarasını artırın
Çözümünüzde ikililerin sürüm numarasını ayarlayın ve her bir güncelleştirmeyle artırın. Bu, kullanıcıların sürümler ve uyumluluk değerlendirmesi arasındaki değişiklikleri belirlemesine daha kolay hale getirir.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Office 'in en son sürümleri için destek deyimleri sağlama
Müşteriler, ISV 'Lerin Office 'te çalışan COM, VSTO ve VBA eklentileri için destek bildirimleri sağlamasını istiyor. Açık destek deyimlerinizi listelemek, Office 365 ProPlus hazırlık araçları 'nı kullanan müşterilerin desteğiniz olduğunu anlamalarına yardımcı olur.

Office istemci uygulamalarına yönelik destek deyimleri sağlamak için (örneğin, Word veya Excel), önce eklentilerinizin geçerli Office sürümünde çalıştırıldığını doğrulayın ve sonra eklenti sonraki bir sürümde kesintiye kesildiğinde güncelleştirmeler sağlamak için yürütün. Microsoft yeni bir yapı veya Office güncelleştirmesi yayımlandığında eklentilerinizi test etmeniz gerekmez. Microsoft, Office 'teki COM, VSTO ve VBA genişletilebilirlik platformunu nadiren değiştirir ve bu değişiklikler iyi şekilde belgelenmiştir.

>Önemli: Microsoft, hazırlık raporları ve ISV iletişim bilgileri için desteklenen eklentilerin bir listesini tutar. Eklentiyi listeye almak için, bkz. [/ConfigMgr/Desktop-anallars/Ready-for-Windows](/configmgr/desktop-analytics/ready-for-windows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Yükleme veya yükleme sorunlarını ayıklamada yardımcı olması için Işlem Izleyicisini kullanın
Eklentilerinizin yükleme veya yükleme sırasında uyumluluk sorunları varsa, bu kişiler dosya veya kayıt defteri erişimiyle ilgili sorunlar ile ilişkili olabilir. Sorunu belirlemenize yardımcı olması için [Işlem izleyicisini](/sysinternals/downloads/procmon) veya benzer bir hata ayıklama aracını kullanarak bir çalışma ortamına karşı davranışı günlüğe kaydedin ve karşılaştırın.
