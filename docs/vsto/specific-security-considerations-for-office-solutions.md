---
title: Güvenlik çözümleri için belirli güvenlik Office dikkat edilmesi gerekenler
description: Microsoft .NET Framework ve Microsoft Office tarafından sağlanan güvenlik özelliklerinin Office tehditlere karşı korumanıza nasıl yardımcı olduğunu öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- troubleshooting Office development in Visual Studio, security
- trusted code [Office development in Visual Studio]
- blocked code [Office development in Visual Studio]
- Outlook [Office development in Visual Studio], object model guard
- malicious code [Office development in Visual Studio]
- Outlook object model guard [Office development in Visual Studio]
- security [Office development in Visual Studio], troubleshooting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 19283a8e0a3749255beee03b95cf26cf28d76c05
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099509"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Güvenlik çözümleri için belirli güvenlik Office dikkat edilmesi gerekenler
  Microsoft .NET Framework ve Microsoft Office tarafından sağlanan güvenlik özellikleri, Office olası güvenlik tehditlerine karşı korumanıza yardımcı olabilir. Bu konu başlığında, bu tehditlerden bazıları açıklanmıştır ve bu tehditlere karşı korunmaya yardımcı olmak için öneriler sağlar. Ayrıca, güvenlik ayarlarının Microsoft Office çözümleri nasıl etkilediği hakkında Office içerir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Güvenilen kod yeni, kötü amaçlı bir belgede yeniden amaçlandırıldı
 Bir saldırgan, bir iş uygulaması için kişisel bilgileri indirme gibi belirli bir amaca yönelik güvenilir kodu alıp çalışma sayfası gibi başka bir belgede yeniden kullanabilir. Kod, özgün belgenin çalışma olmadığını bilmiyor ve farklı bir kullanıcı tarafından açıldığında kişisel bilgileri ortaya çıkarmak veya daha fazla ayrıcalıkla kod yürütme gibi başka tehditler ortaya çıkar. Alternatif olarak, saldırgan çalışma sayfasındaki verileri, kurbana göndererek beklenmedik şekilde davranarak değiştirebilir. Koda bağlı bir çalışma sayfasının değerlerini, formüllerini veya sunum özelliklerini değiştirerek kötü amaçlı bir kullanıcının değiştirilmiş bir dosya göndererek başka bir kullanıcıya saldırması mümkündür. Ayrıca kullanıcıların çalışma sayfasındaki değerleri değiştirerek görmeleri gereken bilgilere erişmesi de mümkündür.

 Hem derleme konumu hem de belge konumu yürütülecek yeterli kanıta sahip olmalıdır, bu saldırının bağlaması kolay değildir. Örneğin, e-posta ekleri veya güvenilmeyen intranet sunucularında belgeler çalıştırmak için yeterli izinlere sahip değildir.

 Bu saldırıyı mümkün hale getirirken kodun kendisine güvenilmeyen verileri temel alan kararlar vermek için kod yazılmalıdır. Örnek olarak veritabanı sunucusunun adını içeren gizli bir hücreye sahip bir çalışma sayfası oluşturulur. Kullanıcı çalışma sayfasını bir ASPX sayfasına gönderir ve bu sayfa, kimlik doğrulaması ve sabit SQL SA parolası kullanarak bu sunucuya bağlanmaya çalışır. Bir saldırgan gizli hücrenin içeriğini farklı bir bilgisayar adıyla değiştirebilir ve SA parolasını edinir. Bu sorunu önlemek için hiçbir zaman parolaları sabit kodlanın ve sunucu kimliklerini her zaman sunucuya erişmeden önce iyi olduğu bilinen iç sunucu listesine karşı kontrol edin.

### <a name="recommendations"></a>Öneriler

- Kullanıcıdan, belgeden, veritabanından, web hizmetlerinden veya başka bir kaynaktan gelen giriş ve verileri her zaman doğrular.

- Kullanıcı adına ayrıcalıklı veriler alma ve korumasız bir çalışma sayfasına ekleme gibi belirli işlev türlerini açığa çıkararak dikkatli olun.

- Uygulamanın türüne bağlı olarak, herhangi bir kod yürütmeden önce özgün belgenin çalıştığını doğrulamak mantıklı olabilir. Örneğin, bunun bilinen ve güvenli bir konumda depolanan bir belgeden çalıştığını doğrulayın.

- Uygulamanız ayrıcalıklı eylemler gerçekleştiriyorsa belge açıldığında bir uyarı görüntülemek iyi bir fikir olabilir. Örneğin, uygulamanın kişisel bilgilere erişecek ve kullanıcının devam ya da iptal etme seçeneğini seçmesini söyleyen bir giriş ekranı veya başlangıç iletişim kutusu oluşturabilirsiniz. Bir son kullanıcı görünen bir belgeden böyle bir uyarı alırsa, herhangi bir şey tehlikeye atmadan önce uygulamadan çıkabilecektir.

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Kod, nesne model Outlook tarafından engellendi
 Microsoft Office nesne modelinde belirli özellikleri, yöntemleri ve nesneleri kullanmalarını kısıtlar. Bu nesnelere erişimi kısıtlayan Outlook e-posta virüslerinin kötü amaçlı olarak nesne modelini kullanmalarını önlemeye yardımcı olur. Bu güvenlik özelliği, nesne Outlook koruma olarak bilinir. VSTO Eklenti, nesne modeli koruma etkinken kısıtlanmış bir özellik veya yöntem kullanmayı denerse, Outlook kullanıcının işlemi durdurması veya kullanıcının sınırlı bir süre için özellik veya yönteme erişim izni verilmesini sağlayan bir güvenlik uyarısı görüntüler. Kullanıcı işlemi durdurursa, Outlook VSTO çözüm kullanılarak oluşturulan Office eklentileri Visual Studio <xref:System.Runtime.InteropServices.COMException> atar.

 Nesne modeli koruma, VSTO ile birlikte kullanılan Outlook bağlı olarak Microsoft Exchange Server:

- Yönetici Outlook ile birlikte Exchange, bilgisayarda tüm uygulama eklentileri için nesne modeli korumasını etkinleştir VSTO veya devre dışı bırakabilirsiniz.

- Outlook Exchange ile birlikte kullanılırsa, yönetici, bilgisayarda tüm VSTO Eklentileri için nesne modeli korumasını etkinleştirerek veya devre dışı bırakarak ya da belirli VSTO Eklentilerinin nesne model korumasıyla karşılaşmadan çalıştırılayamını belirtebilirsiniz. Yöneticiler, nesne modelinin belirli alanları için nesne modeli korumanın davranışını da değiştirebilir. Örneğin, yöneticiler, nesne model VSTO bile otomatik olarak e-posta göndermesine izin VSTO eklentilerinin e-posta göndermesine olanak sağlar.

  2007'Outlook başlayarak, nesne modeli korumanın davranışı, geliştirici ve kullanıcı deneyimini geliştirmek için değiştirilmiştir ve bu sırada bu korumayı güvenli Outlook yardımcı olur. Daha fazla bilgi için [bkz. Outlook 2007'de kod güvenliği değişiklikleri.](/previous-versions/office/developer/office-2007/bb226709(v=office.12))

### <a name="minimize-object-model-guard-warnings"></a>Nesne modeli koruma uyarılarını en aza indirme
 Kısıtlı özellikler ve yöntemler kullanırken güvenlik uyarılarını önlemeye yardımcı olmak için, VSTO Eklentinizin projenizin sınıfındaki alanından Outlook nesnelerini edin `Application` `ThisAddIn` olduğundan emin olun. Bu alan hakkında daha fazla bilgi için [bkz. Program VSTO Eklentileri.](../vsto/programming-vsto-add-ins.md)

 Yalnızca Outlook nesneden alınan nesnelere nesne modeli koruma tarafından güvenebilirsiniz. Buna karşılık, yeni bir nesneden alınan nesnelere güvenilmiyor ve nesne model koruma etkinse kısıtlı özellikler ve yöntemler güvenlik `Microsoft.Office.Interop.Outlook.Application` uyarıları oluşturur.

 Aşağıdaki kod örneği, nesne model koruma etkinse bir güvenlik uyarısı görüntüler. `To`sınıfının özelliği `Microsoft.Office.Interop.Outlook.MailItem` nesne modeli koruması tarafından kısıtlanır. Kod, alandan almak yerine yeni işleci kullanılarak oluşturulan bir nesnesinden elde edildiği için `Microsoft.Office.Interop.Outlook.MailItem` `Microsoft.Office.Interop.Outlook.Application` nesnesine güvenilmeyen bir  `Application` nesnedir.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb" id="Snippet1":::

 Aşağıdaki kod örneği, nesne modeli koruma tarafından güvenilen bir nesnenin kısıtlı To `Microsoft.Office.Interop.Outlook.MailItem` özelliğinin nasıl kullanılageldiğini gösterir. Kod, almak `Application` için güvenilen alanı `Microsoft.Office.Interop.Outlook.MailItem` kullanır.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs" id="Snippet2":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb" id="Snippet2":::

> [!NOTE]
> Outlook Exchange ile birlikte kullanılırsa, Outlook Eklentinizin tüm Outlook nesne modelinin tamamına erişe VSTO nesne `ThisAddIn.Application` modelinin tamamına erişe Outlook garanti edilemez. Örneğin, Exchange yöneticisi Outlook Outlook nesne modelini kullanarak adres bilgilerine erişmeye yönelik tüm girişimleri otomatik olarak reddedecek şekilde Outlook ayarlarsa, kod örneği güvenilen alanı kullansa bile önceki kod örneğinin To özelliğine erişmesine izin `ThisAddIn.Application` vermez.

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Uygulama kullanırken hangi Eklentilerin güven Exchange
 Yöneticiler Outlook ile birlikte Exchange, bazı VSTO'ların nesne model korumasıyla karşılaşmadan çalıştırılayamlarını belirtebilirsiniz. Outlook VSTO çözümler kullanılarak oluşturulan Office tek Visual Studio tek güvenilemez; yalnızca bir grup olarak güvenilir.

 Outlook eklentinin VSTO noktası DLL'sinde karma koda dayalı olarak bir eklentiye VSTO güvener. Tüm Outlook VSTO aynı giriş noktası DLL'sini [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] (VSTOLoader.dll)*kullanmayı hedeflemiştir.* Bu, bir yönetici nesne modeli koruma ile karşılaşmadan çalıştıracak şekilde hedef alan herhangi bir VSTO Eklentiye güvenirse, hedefini hedef alan diğer tüm VSTO eklentilerine de [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] güvendiği anlamına gelir. Nesne modeli koruma ile karşılaşmadan VSTO eklentilerinin çalışmasına güvenme hakkında daha fazla bilgi için bkz. Virüs önleme özelliklerini yönetmek için Outlook yöntemini [belirtme.](/previous-versions/office/office-2007-resource-kit/cc179194(v=office.12))

## <a name="permission-changes-do-not-take-effect-immediately"></a>İzin değişiklikleri hemen etkili olmaz
 Yönetici bir belge veya derleme için izinleri ayarlarsa, kullanıcıların bu değişikliklerin uygulanması için tüm Office uygulamaları yeniden başlatması gerekir.

 Bu uygulamaları Microsoft Office diğer uygulamalar da yeni izinlerin uygulanmasını önlenebilir. Kullanıcılar, güvenlik ilkeleri değiştir Office, barındırılan veya tek başına uygulamaları kullanan tüm uygulamalardan çıkmalıdır.

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Microsoft Office sistemi Microsoft Office merkezi ayarları, Eklentileri veya belge düzeyi özelleştirmeleri etkilemez
 Kullanıcılar, VSTO Merkezi'nde bir seçenek ayarerek eklentilerin yüklenmesini **önlenebilir.** Ancak VSTO çözümleri kullanılarak oluşturulan ek eklentiler ve belge Office özelleştirmeler Visual Studio güven ayarlarından etkilenmez.

 Kullanıcı, VSTO Merkezi'ne kullanarak eklentilerin yüklenmesini önlese **de,** aşağıdaki VSTO türler yüklenmez:

- Yönetilen ve yönetilemeyen COM VSTO eklentileri.

- Yönetilen ve yönetilemeyen akıllı belgeler.

- Yönetilen ve yönetilemeyen Otomasyon VSTO eklentileri.

- Yönetilen ve yönetilemeyen gerçek zamanlı veri bileşenleri.

  Aşağıdaki yordamlar, kullanıcıların Microsoft'ta ve VSTO  [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 2010'da Microsoft Office kullanmayı açıklar. Bu yordamlar, VSTO geliştirme araçları kullanılarak oluşturulan Office eklentileri veya özelleştirmeleri Visual Studio.

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-office_15_short-applications"></a>VSTO 2010 ve Microsoft uygulamalarında Microsoft Office devre dışı bırakmak [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] için

1. Dosya **sekmesini** seçin.

2. *ApplicationName Seçenekleri* **düğmesini** seçin.

3. Kategoriler bölmesinde Güven **Merkezi'ni seçin.**

4. Ayrıntılar bölmesinde Güven **Merkezi'ni seçin ve Ayarlar.**

5. Kategoriler bölmesinde **Eklentiler'i seçin.**

6. Ayrıntılar bölmesinde, Uygulama **Eklentilerini** Güvenilen Eklentiler tarafından İmzalanacak Şekilde Gerektir'i Publisher Veya Tüm Uygulama **Eklentilerini Devre Dışı Bırak'ı seçin.**

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
