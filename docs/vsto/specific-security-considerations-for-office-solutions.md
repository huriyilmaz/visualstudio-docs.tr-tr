---
title: Office çözümleri için belirli güvenlik konuları
description: Microsoft .NET Framework ve Microsoft Office tarafından sağlanan güvenlik özelliklerinin güvenlik tehditlerine karşı Office çözümlerinizi korumanıza nasıl yardımcı olabileceğini öğrenin.
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
ms.openlocfilehash: 76d47af6c0a2c20fd80c9e83275f5a083e9ce899d98e079a28ac710355e0f6de
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121423858"
---
# <a name="specific-security-considerations-for-office-solutions"></a>Office çözümleri için belirli güvenlik konuları
  Microsoft .NET Framework ve Microsoft Office tarafından sağlanan güvenlik özellikleri, Office çözümlerinizi olası güvenlik tehditlerine karşı korumanıza yardımcı olabilir. Bu konu, bu tehditlerin bazılarını açıklar ve bunlara karşı koruma sağlamaya yardımcı olmak için öneriler sağlar. ayrıca, Microsoft Office güvenlik ayarlarının Office çözümlerini nasıl etkilediği hakkında bilgi içerir.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="trusted-code-is-repurposed-in-a-new-malicious-document"></a>Güvenilen kod yeni, kötü amaçlı bir belgede yeniden tasarlanmıştır
 Bir saldırgan, belirli bir amaç için özel bir amaç (örneğin, bir istihdam uygulamasının kişisel bilgilerini indirmek) ve onu çalışma sayfası gibi başka bir belgede yeniden kullanmak için bir güvenilen kod alabilir. Kod, özgün belgenin çalışmadığını bilmez ve farklı bir kullanıcı tarafından açıldığında, kişisel bilgiler veya artan ayrıcalıklarla kod yürütme gibi diğer tehditleri açabilir. Alternatif olarak, saldırgan çalışma sayfasındaki verileri, kurban 'e gönderildiğinde beklenmedik bir şekilde davrandığı gibi değiştirebilir. Kod ile bağlantılı bir çalışma sayfasının değerlerini, formüllerini veya sunu özelliklerini değiştirerek, kötü niyetli bir kullanıcının değiştirilmiş bir dosyayı göndererek başka bir kullanıcıya saldırmasını mümkündür. Ayrıca, çalışma sayfasındaki değerleri değiştirerek kullanıcıların görmedikleri bilgilere erişebilmeleri de mümkün olabilir.

 Hem derleme konumu hem de belge konumunun yürütülmesi için yeterli kanıt olması gerektiğinden, bu saldırının bağlanması kolay değildir. Örneğin, e-posta ekleri veya güvenilmeyen intranet sunucularındaki belgeler çalıştırmak için yeterli izinlere sahip değildir.

 Bu saldırıyı mümkün kılmak için kodun kendisi, potansiyel olarak güvenilir olmayan verilere göre kararlar verecek şekilde yazılmalıdır. Bir veritabanı sunucusunun adını içeren gizli bir hücre içeren bir çalışma sayfası oluşturma örneği. kullanıcı çalışma sayfasını, SQL kimlik doğrulaması ve sabit kodlanmış bir SA parolası kullanarak bu sunucuya bağlanmayı deneyen bir ASPX sayfasına gönderir. Saldırgan, gizli hücrenin içeriğini farklı bir bilgisayar adıyla değiştirebilir ve SA parolasını alabilir. Bu sorundan kaçınmak için, hiçbir zaman kalıcı olarak parola kodu ve sunucu kimliklerini sunucuya erişmeden önce iyi olduğu bilinen bir iç sunucu listesine karşı denetleyin.

### <a name="recommendations"></a>Öneriler

- Kullanıcı, belge, veritabanı, Web hizmeti veya diğer kaynaklardan gelen giriş ve verileri her zaman doğrulayın.

- Kullanıcı adına ayrıcalıklı verileri alma ve bunu korumasız bir çalışma sayfasına yerleştirme gibi belirli işlevsellik türlerini açığa çıkarmak konusunda dikkatli olun.

- Uygulamanın türüne bağlı olarak, herhangi bir kodu yürütmeden önce orijinal belgenin çalıştığını doğrulamak mantıklı olabilir. Örneğin, bilinen, güvenli bir konumda depolanan bir belgeden çalıştığını doğrulayın.

- Uygulamanız ayrıcalıklı eylemler gerçekleştirdiğinde belge açıldığında bir uyarı görüntülenmesi iyi bir fikir olabilir. Örneğin, uygulamanın kişisel bilgilere erişebileceğini ve kullanıcının devam etmeyi veya iptal etmeyi seçmesini belirten bir giriş ekranı veya bir başlangıç iletişim kutusu oluşturabilirsiniz. Bir son kullanıcı bir yazmasum belgesinden böyle bir uyarı alırsa, hiçbir şeyin tehlikeye atılmadan önce uygulamadan çıkabilirsiniz.

## <a name="code-is-blocked-by-the-outlook-object-model-guard"></a>kod, Outlook nesne modeli koruyucusu tarafından engelleniyor
 Microsoft Office, nesne modelindeki belirli özellikleri, yöntemleri ve nesneleri kullanarak kodu kısıtlayabilir. bu nesnelere erişimi kısıtlayarak Outlook, e-posta solucanlarının ve virüslerin kötü amaçlı amaçlarla nesne modelini kullanmasını önlemeye yardımcı olur. bu güvenlik özelliği Outlook nesne modeli koruyucusu olarak bilinir. bir VSTO eklentisi, nesne modeli koruyucusu etkinken kısıtlı bir özellik veya yöntem kullanmaya çalışırsa, Outlook kullanıcının işlemi durdurmasına olanak tanıyan bir güvenlik uyarısı görüntüler veya kullanıcının sınırlı bir süre için özelliğe veya yönteme erişim izni vermesini sağlar. kullanıcı işlemi durdurduktan sonra Visual Studio içindeki Office çözümleri kullanılarak oluşturulan Outlook VSTO eklentileri bir oluşturur <xref:System.Runtime.InteropServices.COMException> .

 nesne modeli koruyucusu, Outlook Microsoft Exchange Server ile kullanılıp kullanıldığına bağlı olarak farklı yollarla VSTO eklentilerini etkileyebilir:

- Outlook Exchange birlikte kullanılmazsa, yönetici bilgisayardaki tüm VSTO eklentileri için nesne modeli koruyucusunu etkinleştirebilir veya devre dışı bırakabilir.

- Outlook Exchange ile kullanılırsa, yönetici bilgisayardaki tüm VSTO eklentileri için nesne modeli koruyucusunu etkinleştirebilir veya devre dışı bırakabilir ya da yönetici, belirli VSTO eklentilerin nesne modeli koruyucusu olmadan çalıştırılabilirler. Yöneticiler, nesne modelinin belirli alanlarında nesne modeli koruyucusu davranışını de değiştirebilir. örneğin, yöneticiler, nesne modeli koruyucusu etkin olsa bile, VSTO eklentilerin otomatik olarak e-posta göndermesini sağlayabilir.

  Outlook 2007 ' den başlayarak, nesne modeli koruyucusu davranışı, Outlook güvenli tutmaya yardımcı olurken geliştirici ve kullanıcı deneyimini geliştirmek üzere değiştirilmiştir. daha fazla bilgi için [Outlook 2007 ' de kod güvenliği değişiklikleri](/previous-versions/office/developer/office-2007/bb226709(v=office.12))bölümüne bakın.

### <a name="minimize-object-model-guard-warnings"></a>Nesne modeli koruyucu uyarılarını Simgeleştir
 kısıtlı özellikler ve yöntemler kullandığınızda güvenlik uyarılarını önlemeye yardımcı olmak için VSTO eklentisinin `Application` projenizdeki sınıfın alanından Outlook nesneleri edindiğinizden emin olun `ThisAddIn` . bu alan hakkında daha fazla bilgi için bkz. [Program VSTO eklentileri](../vsto/programming-vsto-add-ins.md).

 yalnızca bu nesneden elde edilen Outlook nesneler nesne modeli koruyucusu tarafından güvenilir olabilir. Buna karşılık, yeni bir nesneden edinilen nesneler `Microsoft.Office.Interop.Outlook.Application` güvenilir değildir ve nesne modeli koruyucusu etkinse kısıtlı özellikler ve Yöntemler güvenlik uyarıları oluşturacak.

 Aşağıdaki kod örneği, nesne modeli koruyucusu etkinse bir güvenlik uyarısı görüntüler. `To`Sınıfının özelliği, `Microsoft.Office.Interop.Outlook.MailItem` nesne modeli koruyucusu tarafından kısıtlanır. `Microsoft.Office.Interop.Outlook.MailItem`Kodu `Microsoft.Office.Interop.Outlook.Application` alanından almak yerine **Yeni** işleç kullanılarak oluşturulan bir öğesinden aldığından, nesne güvenli değildir `Application` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb" id="Snippet1":::

 Aşağıdaki kod örneği, `Microsoft.Office.Interop.Outlook.MailItem` nesne modeli koruyucusu tarafından güvenilen bir nesnenin kısıtlı to özelliğinin nasıl kullanılacağını gösterir. Kod, ' i `Application` almak için güvenilir alanını kullanır `Microsoft.Office.Interop.Outlook.MailItem` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreOutlookSecurity/ThisAddIn.cs" id="Snippet2":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreOutlookSecurity/ThisAddIn.vb" id="Snippet2":::

> [!NOTE]
> Outlook Exchange ile kullanılırsa, ' den tüm Outlook nesneleri elde etmek `ThisAddIn.Application` VSTO eklentisinin tüm Outlook nesne modeline erişebilmesini garantilemez. örneğin, bir Exchange yönetici Outlook nesne modelini kullanarak adres bilgilerine erişme girişimlerini otomatik olarak reddedecek Outlook Outlook, kod örneği güvenilir alanı kullansa bile, önceki kod örneğine erişim izni vermez `ThisAddIn.Application` .

### <a name="specify-which-add-ins-to-trust-when-using-exchange"></a>Exchange kullanırken hangi eklentilerin güveneceği belirtin
 Outlook Exchange kullanılırken yöneticiler, belirli VSTO eklentilerin nesne modeli koruyucusu ile karşılaşmadan çalıştırılabilirler. Visual Studio Office çözümleri kullanılarak oluşturulan Outlook VSTO eklentileri ayrı ayrı güvenilemez; yalnızca Grup olarak güvenilir olabilir.

 Outlook, VSTO eklentisinin giriş noktası DLL 'inin karma koduna göre VSTO bir eklentiye güvenir. ' ı hedefleyen tüm Outlook VSTO eklentileri [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aynı giriş noktası DLL 'sini (*VSTOLoader.dll*) kullanır. bu, bir yönetici, nesne modeli koruyucusu ile karşılaşılmadan çalıştırmak için ' i hedefleyen herhangi bir VSTO eklentiye güveniyorsa [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] , öğesini hedefleyen diğer tüm VSTO eklentileri [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] de güvenilirdir. belirli VSTO eklentilerin nesne modeli koruyucusu ile karşılaşmadan çalışmasına güvenme hakkında daha fazla bilgi için, bkz. [virüs önleme özelliklerini yönetmek için kullanılan yöntemi belirtin Outlook](/previous-versions/office/office-2007-resource-kit/cc179194(v=office.12)).

## <a name="permission-changes-do-not-take-effect-immediately"></a>İzin değişiklikleri hemen etkili olmaz
 yönetici bir belge veya derleme için izinleri ayarladığında, kullanıcılar bu değişikliklerin uygulanması için tüm Office uygulamalarını sonlandırmalıdır ve sonra yeniden başlatmalıdır.

 Microsoft Office uygulamaları barındıran diğer uygulamalar da yeni izinlerin uygulanmasını engelleyebilir. kullanıcılar, güvenlik ilkeleri değiştirildiğinde Office, barındırılan veya tek başına kullanan tüm uygulamalardan çıkmalıdır.

## <a name="trust-center-settings-in-the-microsoft-office-system-do-not-affect-add-ins-or-document-level-customizations"></a>Microsoft Office sistemindeki güven merkezi ayarları, eklentileri veya belge düzeyi özelleştirmelerini etkilemez
 kullanıcılar, **güven merkezi**'nde bir seçenek ayarlayarak VSTO eklentilerin yüklenmesini engelleyebilir. ancak, Visual Studio Office çözümleri kullanılarak oluşturulan eklentiler ve belge düzeyi özelleştirmeleri, bu güven ayarlarından etkilenmez VSTO.

 kullanıcı VSTO eklentilerin **güven merkezini** kullanarak yüklenmesini engelliyorsa, aşağıdaki türlerde VSTO eklentiler yüklenmez:

- yönetilen ve yönetilmeyen COM VSTO eklentileri.

- Yönetilen ve yönetilmeyen akıllı belgeler.

- yönetilen ve yönetilmeyen otomasyon VSTO eklentileri.

- Yönetilen ve yönetilmeyen gerçek zamanlı veri bileşenleri.

  aşağıdaki yordamlarda, kullanıcıların Microsoft ve Microsoft Office 2010 VSTO eklentilerin yüklenmesini kısıtlamak için **güven merkezini** nasıl kullanabileceği açıklanır [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] . bu yordamlar, Visual Studio Office geliştirme araçları kullanılarak oluşturulan eklentileri veya özelleştirmeleri VSTO etkilemez.

#### <a name="to-disable-vsto-add-ins-in-microsoft-office-2010-and-microsoft-office_15_short-applications"></a>Microsoft Office 2010 ve Microsoft uygulamalarında VSTO eklentileri devre dışı bırakmak için [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)]

1. **Dosya** sekmesini seçin.

2. *ApplicationName* **seçenekleri** düğmesini seçin.

3. Kategoriler bölmesinde **Güven Merkezi**' ni seçin.

4. ayrıntılar bölmesinde **güven merkezi Ayarlar**' ni seçin.

5. Kategoriler bölmesinde, **Eklentiler**' i seçin.

6. ayrıntılar bölmesinde, **uygulama eklentilerinin güvenilir Publisher imzalanması** veya **tüm uygulama eklentilerini devre dışı bırak**' ı seçin.

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümleri güvenli hale getirme](../vsto/securing-office-solutions.md)
