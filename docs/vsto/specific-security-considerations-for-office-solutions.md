---
title: Office çözümleri için belirli güvenlik konuları
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 571b604b87fb7fac4e78c83a791c265d910fae94
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985588"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Office çözümleri için belirli güvenlik konuları
  Microsoft .NET Framework ve Microsoft Office tarafından sağlanan güvenlik özellikleri, Office çözümlerinizi olası güvenlik tehditlerine karşı korumaya yardımcı olabilir. Bu konu, bu tehditlerin bazılarını açıklar ve bunlara karşı koruma sağlamaya yardımcı olmak için öneriler sağlar. Ayrıca, Microsoft Office güvenlik ayarlarının Office çözümlerini nasıl etkilediği hakkında bilgi içerir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Güvenilen kod yeni, kötü amaçlı bir belgede yeniden tasarlanmıştır
 Bir saldırgan, belirli bir amaç için özel bir amaç (örneğin, bir istihdam uygulamasının kişisel bilgilerini indirmek) ve onu çalışma sayfası gibi başka bir belgede yeniden kullanmak için bir güvenilen kod alabilir. Kod, özgün belgenin çalışmadığını bilmez ve farklı bir kullanıcı tarafından açıldığında, kişisel bilgiler veya artan ayrıcalıklarla kod yürütme gibi diğer tehditleri açabilir. Alternatif olarak, saldırgan çalışma sayfasındaki verileri, kurban 'e gönderildiğinde beklenmedik bir şekilde davrandığı gibi değiştirebilir. Kod ile bağlantılı bir çalışma sayfasının değerlerini, formüllerini veya sunu özelliklerini değiştirerek, kötü niyetli bir kullanıcının değiştirilmiş bir dosyayı göndererek başka bir kullanıcıya saldırmasını mümkündür. Ayrıca, çalışma sayfasındaki değerleri değiştirerek kullanıcıların görmedikleri bilgilere erişebilmeleri de mümkün olabilir.

 Hem derleme konumu hem de belge konumunun yürütülmesi için yeterli kanıt olması gerektiğinden, bu saldırının bağlanması kolay değildir. Örneğin, e-posta ekleri veya güvenilmeyen intranet sunucularındaki belgeler çalıştırmak için yeterli izinlere sahip değildir.

 Bu saldırıyı mümkün kılmak için kodun kendisi, potansiyel olarak güvenilir olmayan verilere göre kararlar verecek şekilde yazılmalıdır. Bir veritabanı sunucusunun adını içeren gizli bir hücre içeren bir çalışma sayfası oluşturma örneği. Kullanıcı çalışma sayfasını, SQL kimlik doğrulaması kullanarak bu sunucuya bağlanmayı deneyen bir ASPX sayfasına gönderir ve sabit kodlanmış bir SA parolası. Saldırgan, gizli hücrenin içeriğini farklı bir bilgisayar adıyla değiştirebilir ve SA parolasını alabilir. Bu sorundan kaçınmak için, hiçbir zaman kalıcı olarak parola kodu ve sunucu kimliklerini sunucuya erişmeden önce iyi olduğu bilinen bir iç sunucu listesine karşı denetleyin.

### <a name="recommendations"></a>Öneri

- Kullanıcı, belge, veritabanı, Web hizmeti veya diğer kaynaklardan gelen giriş ve verileri her zaman doğrulayın.

- Kullanıcı adına ayrıcalıklı verileri alma ve bunu korumasız bir çalışma sayfasına yerleştirme gibi belirli işlevsellik türlerini açığa çıkarmak konusunda dikkatli olun.

- Uygulamanın türüne bağlı olarak, herhangi bir kodu yürütmeden önce orijinal belgenin çalıştığını doğrulamak mantıklı olabilir. Örneğin, bilinen, güvenli bir konumda depolanan bir belgeden çalıştığını doğrulayın.

- Uygulamanız ayrıcalıklı eylemler gerçekleştirdiğinde belge açıldığında bir uyarı görüntülenmesi iyi bir fikir olabilir. Örneğin, uygulamanın kişisel bilgilere erişebileceğini ve kullanıcının devam etmeyi veya iptal etmeyi seçmesini belirten bir giriş ekranı veya bir başlangıç iletişim kutusu oluşturabilirsiniz. Bir son kullanıcı bir yazmasum belgesinden böyle bir uyarı alırsa, hiçbir şeyin tehlikeye atılmadan önce uygulamadan çıkabilirsiniz.

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>Kod Outlook nesne modeli koruyucusu tarafından engelleniyor
 Microsoft Office, nesne modelindeki belirli özellikleri, yöntemleri ve nesneleri kullanarak kodu kısıtlayabilir. Outlook, bu nesnelere erişimi kısıtlayarak e-posta solucanlarının ve virüslerin kötü amaçlı olarak nesne modelini kullanmasını önlemeye yardımcı olur. Bu güvenlik özelliği Outlook nesne modeli koruyucusu olarak bilinir. Bir VSTO eklentisi, nesne modeli koruyucusu etkinken kısıtlı bir özellik veya yöntem kullanmaya çalışırsa, Outlook, kullanıcının işlemi durdurmasına izin veren bir güvenlik uyarısı görüntüler veya kullanıcının sınırlı bir süre için özelliğe veya yönteme erişim izni vermesini sağlar IME. Kullanıcı işlemi durdurduktan sonra, Visual Studio 'da Office çözümleri kullanılarak oluşturulan Outlook VSTO eklentileri bir <xref:System.Runtime.InteropServices.COMException>oluşturur.

 Nesne modeli koruyucusu, Outlook 'un Microsoft Exchange Server ile kullanılıp kullanıldığına bağlı olarak VSTO Eklentilerini farklı yollarla etkileyebilir:

- Outlook Exchange ile kullanılmazsa, yönetici bilgisayardaki tüm VSTO eklentileri için nesne modeli koruyucusunu etkinleştirebilir veya devre dışı bırakabilir.

- Outlook Exchange ile kullanılıyorsa, yönetici bilgisayardaki tüm VSTO eklentileri için nesne modeli koruyucusunu etkinleştirebilir veya devre dışı bırakabilir ya da yönetici, belirli VSTO eklentilerinin nesne modeli koruyucusu ile karşılaşmadan çalıştırılabilirler. Yöneticiler, nesne modelinin belirli alanlarında nesne modeli koruyucusu davranışını de değiştirebilir. Örneğin, Yöneticiler, nesne modeli koruyucusu etkin olsa bile, VSTO eklentilerinin otomatik olarak e-posta göndermesini sağlayabilir.

  Outlook 2007 ' den başlayarak, nesne modeli koruyucusu davranışı, Outlook güvenliğini sağlamaya yardımcı olurken geliştirici ve Kullanıcı deneyimini geliştirmek üzere değiştirilmiştir. Daha fazla bilgi için bkz. [Outlook 2007 'Deki kod güvenliği değişiklikleri](/previous-versions/office/developer/office-2007/bb226709(v=office.12)).

### <a name="minimize-object-model-guard-warnings"></a>Nesne modeli koruyucu uyarılarını Simgeleştir
 Kısıtlanmış Özellikler ve Yöntemler kullandığınızda güvenlik uyarılarından kaçınmak için, VSTO eklentisinin projenizdeki `ThisAddIn` sınıfının `Application` alanından Outlook nesnelerini edindiğinizden emin olun. Bu alan hakkında daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

 Yalnızca bu nesneden edinilen Outlook nesnelerine nesne modeli koruyucusu tarafından güveniliyor. Buna karşılık, yeni bir `Microsoft.Office.Interop.Outlook.Application` nesnesinden elde edilen nesneler güvenilir değildir ve nesne modeli koruyucusu etkinse kısıtlı özellikler ve Yöntemler güvenlik uyarıları oluşturacak.

 Aşağıdaki kod örneği, nesne modeli koruyucusu etkinse bir güvenlik uyarısı görüntüler. `Microsoft.Office.Interop.Outlook.MailItem` sınıfının `To` özelliği, nesne modeli koruyucusu tarafından kısıtlanır. `Microsoft.Office.Interop.Outlook.MailItem` nesnesi güvenilir değil çünkü kod, `Application` alandan almak yerine **Yeni** işleç kullanılarak oluşturulan bir `Microsoft.Office.Interop.Outlook.Application` alır.

 [!code-csharp[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#1)]
 [!code-vb[Trin_VstcoreOutlookSecurity#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#1)]

 Aşağıdaki kod örneği, nesne modeli koruyucusu tarafından güvenilen bir `Microsoft.Office.Interop.Outlook.MailItem` nesnesinin kısıtlanmış to özelliğinin nasıl kullanılacağını gösterir. Kod, `Microsoft.Office.Interop.Outlook.MailItem`almak için güvenilir `Application` alanını kullanır.

 [!code-csharp[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs#2)]
 [!code-vb[Trin_VstcoreOutlookSecurity#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb#2)]

> [!NOTE]
> Outlook Exchange ile kullanılıyorsa, tüm Outlook nesnelerini `ThisAddIn.Application` alma işlemi, VSTO eklentisinin tüm Outlook nesne modeline erişebilmesini garantilemez. Örneğin, bir Exchange Yöneticisi Outlook 'u Outlook nesne modeli kullanarak adres bilgilerine erişme girişimlerini otomatik olarak reddedecek şekilde ayarladıysanız, kod örneği tarafından kullanılsa bile, Outlook önceki kod örneğine erişim izni vermez güvenilir `ThisAddIn.Application` alanı.

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Exchange kullanılırken hangi eklentilerin güveneceği belirtin
 Outlook Exchange ile kullanıldığında, Yöneticiler belirli VSTO eklentilerinin nesne modeli koruyucusu ile karşılaşmadan çalıştırılabilirler. Visual Studio 'da Office çözümleri kullanılarak oluşturulan Outlook VSTO eklentilerine tek tek güvenilemez; yalnızca Grup olarak güvenilir olabilir.

 Outlook, VSTO eklentisinin giriş noktası DLL 'inin karma kodunu temel alarak bir VSTO eklentisini güvenir. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] hedefleyen tüm Outlook VSTO eklentileri aynı giriş noktası DLL 'ini (*VSTOLoader. dll*) kullanır. Bu, bir yönetici, nesne modeli koruyucusu ile karşılaşmadan çalıştırmak üzere [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] hedefleyen herhangi bir VSTO eklentisinin güvendiği, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] hedefleyen diğer tüm VSTO eklentileri de güvenilirdir. Nesne modeli koruyucusu ile karşılaşılmadan çalıştırılacak belirli VSTO Eklentilerini güvenme hakkında daha fazla bilgi için, bkz. [Outlook 'un virüs önleme özelliklerini yönetmek için kullandığı yöntemi belirtme](/previous-versions/office/office-2007-resource-kit/cc179194(v=office.12)).

## <a name="permission-changes-do-not-take-effect-immediately"></a>İzin değişiklikleri hemen etkili olmaz
 Yönetici bir belge veya derleme için izinleri ayarladığında, kullanıcıların bu değişikliklerin uygulanması için tüm Office uygulamalarını sonlandırmalıdır ve sonra yeniden başlatması gerekir.

 Microsoft Office uygulamaları barındıran diğer uygulamalar da yeni izinlerin uygulanmasını engelleyebilir. Kullanıcılar, güvenlik ilkeleri değiştirildiğinde Office, barındırılan veya tek başına kullanan tüm uygulamalardan çıkmalıdır.

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Microsoft Office sistemindeki güven Merkezi ayarları, eklentileri veya belge düzeyi özelleştirmelerini etkilemez
 Kullanıcılar, **Güven Merkezi**'nde bir seçenek ayarlayarak VSTO eklentilerinin yüklenmesini engelleyebilir. Ancak, Visual Studio 'da Office çözümleri kullanılarak oluşturulan VSTO eklentileri ve belge düzeyi özelleştirmeleri bu güven ayarlarından etkilenmez.

 Kullanıcı, VSTO eklentilerinin **güven merkezini**kullanarak yüklenmesini engelliyorsa, aşağıdaki VSTO eklentileri türleri yüklenmeyecektir:

- Yönetilen ve yönetilmeyen COM VSTO eklentileri.

- Yönetilen ve yönetilmeyen akıllı belgeler.

- Yönetilen ve yönetilmeyen Otomasyon VSTO eklentileri.

- Yönetilen ve yönetilmeyen gerçek zamanlı veri bileşenleri.

  Aşağıdaki yordamlarda, kullanıcıların Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] ve Microsoft Office 2010 ' de VSTO Eklentilerini yüklemesini kısıtlamak için **güven merkezini** nasıl kullanabileceği açıklanır. Bu yordamlar, Visual Studio 'da Office geliştirme araçları kullanılarak oluşturulan VSTO Eklentilerini veya özelleştirmelerini etkilemez.

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-includeoffice_15_shortvstoincludesoffice-15-short-mdmd-applications"></a>Microsoft Office 2010 ve Microsoft [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] uygulamalarında VSTO eklentilerini devre dışı bırakmak için

1. **Dosya** sekmesini seçin.

2. *ApplicationName* **seçenekleri** düğmesini seçin.

3. Kategoriler bölmesinde **Güven Merkezi**' ni seçin.

4. Ayrıntılar bölmesinde **Güven Merkezi ayarları**' nı seçin.

5. Kategoriler bölmesinde, **Eklentiler**' i seçin.

6. Ayrıntılar bölmesinde, **Uygulama Eklentilerinin Güvenilen yayımcı tarafından Imzalanmasını gerektir** veya **tüm uygulama eklentilerini devre dışı bırak**' ı seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Güvenli Office çözümleri](../vsto/securing-office-solutions.md)
