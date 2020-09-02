---
title: ClickOnce uygulamalarını yerelleştirme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- WPF, ClickOnce applications
- ClickOnce deployment, globalization
- deploying applications [ClickOnce], localizing ClickOnce applications
- localization, ClickOnce deployment
- ClickOnce deployment, download on-demand
- ClickOnce deployment, localization
- Windows Forms, ClickOnce applications
- console applications, ClickOnce applications
ms.assetid: c92b193b-054d-4923-834b-d4226a4c7a1a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 81ee263b3bb908daace4bf27f86cff710ae90684
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64800373"
---
# <a name="localize-clickonce-applications"></a>ClickOnce uygulamalarını yerelleştirme
Yerelleştirme, uygulamanızı belirli bir kültür için uygun hale getirme işlemidir. Bu işlem, Kullanıcı arabirimi (UI) metnini bölgeye özgü bir dile çevirmeyi, doğru tarih ve para birimi biçimlendirmesini kullanarak, form üzerindeki denetimlerin boyutunu ayarlamayı ve gerekirse denetimleri sağdan sola yansıtmayı içerir.

 Uygulamanızı yerelleştirme bir veya daha fazla uydu derlemesi oluşturulmasına neden olur. Her derleme, Kullanıcı arabirimi dizelerini, görüntüleri ve belirli bir kültüre özgü diğer kaynakları içerir. (Uygulamanızın ana yürütülebilir dosyası, uygulamanız için varsayılan kültüre yönelik dizeleri içerir.)

 Bu konuda, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] diğer kültürler için bir uygulamayı dağıtmanın üç yolu açıklanmaktadır:

- Tüm uydu derlemelerini tek bir dağıtıma dahil edin.

- Her kültür için, her birine dahil olan tek bir uydu derlemesi ile bir dağıtım oluşturun.

- Uydu derlemelerini isteğe bağlı olarak indirin.

## <a name="including-all-satellite-assemblies-in-a-deployment"></a>Tüm uydu derlemelerini bir dağıtıma dahil etme
 Birden çok dağıtımı yayımlamak yerine [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] , [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Tüm uydu derlemelerini içeren tek bir dağıtım yayımlayabilirsiniz.

 Bu yöntem, içindeki varsayılandır [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Bu yöntemi içinde kullanmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ek bir iş yapmanız gerekmez.

 Bu yöntemi *MageUI.exe*kullanmak için, uygulamanız için kültürü *MageUI.exe* **bağımsız** olarak ayarlamanız gerekir. Ardından, tüm uydu derlemelerini dağıtımınıza el ile eklemeniz gerekir. *MageUI.exe*, uygulama bildiriminizde **dosyalar** sekmesindeki **doldur** düğmesini kullanarak uydu derlemelerini ekleyebilirsiniz.

 Bu yaklaşımın avantajı, tek bir dağıtım oluşturup yerelleştirilmiş dağıtım hikayenizi basitleştirmesidir. Çalışma zamanında, kullanıcının Windows işletim sisteminin varsayılan kültürüne bağlı olarak uygun uydu derlemesi kullanılacaktır. Bu yaklaşımın bir dezavantajı, uygulama her yüklendiğinde veya bir istemci bilgisayara güncelleştirildiğinde tüm uydu derlemelerini indirmesidir. Uygulamanızda çok sayıda dize varsa veya müşterilerinizin yavaş bir ağ bağlantısı varsa, bu işlem uygulama güncelleştirmesi sırasında performansı etkileyebilir.

> [!NOTE]
> Bu yaklaşım, uygulamanızın farklı kültürlerde farklı metin dizesi boyutlarına uyum sağlamak üzere denetimlerin yüksekliğini, genişliğini ve konumunu otomatik olarak ayarladığını varsayar. Windows Forms, formunuzu <xref:System.Windows.Forms.FlowLayoutPanel> ve denetimleri ve özelliği de dahil olmak üzere kolayca yerelleştirilebilir hale getirmek için formunuzun tasarımını sağlayan çeşitli denetimler ve teknolojiler içerir <xref:System.Windows.Forms.TableLayoutPanel> <xref:System.Windows.Forms.Control.AutoSize%2A> .  Ayrıca bkz. [nasıl yapılır: otomatik AutoSize ve TableLayoutPanel denetimini kullanarak Windows Forms 'ta yerelleştirmeyi destekleme](/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100)).

## <a name="generate-one-deployment-for-each-culture"></a>Her kültür için bir dağıtım oluştur
 Bu dağıtım stratejisinde birden çok dağıtım oluşturursunuz. Her dağıtımda, yalnızca belirli bir kültür için gereken uydu derlemesini dahil edersiniz ve dağıtımı bu kültüre özel olarak işaretlersiniz.

 Bu yöntemi içinde kullanmak için [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Yayımla** sekmesinde **Yayımla dili** özelliğini istenen bölgeye ayarlayın. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , seçtiğiniz bölge için gereken uydu derlemesini otomatik olarak ekler ve diğer tüm uydu derlemelerini dağıtımdan hariç bırakır.

 Aynı şeyi Microsoft 'taki *MageUI.exe* aracını kullanarak gerçekleştirebilirsiniz [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Uygulama dizininden diğer tüm uydu derlemelerini hariç tutmak için uygulama bildiriminizde bulunan **dosyalar** sekmesindeki **doldur** düğmesini kullanın ve ardından *MageUI.exe*' de dağıtım bildiriminiz için **ad** sekmesinde **kültür** alanını ayarlayın. Bu adımlar yalnızca doğru uydu derlemesini içermez, ancak aynı zamanda `language` `assemblyIdentity` dağıtım bildiriminizde öğe üzerindeki özniteliği ilgili kültür olarak ayarlar.

 Uygulamayı yayımladıktan sonra, uygulamanızın desteklediği her ek kültür için bu adımı tekrarlamalısınız. Her uygulama bildirimi farklı bir uydu derlemesine başvuracağı ve her dağıtım bildiriminin öznitelik için farklı bir değere sahip olacağı için, her seferinde farklı bir Web sunucusu dizinine veya dosya paylaşma dizinine yayımladığınızdan emin olmanız gerekir `language` .

## <a name="download-satellite-assemblies-on-demand"></a>İsteğe bağlı uydu derlemelerini indirme
 Tüm uydu derlemelerini tek bir dağıtıma eklemeye karar verirseniz, derlemeleri isteğe bağlı olarak işaretlemenizi sağlayan isteğe bağlı indirmeyi kullanarak performansı artırabilirsiniz. İşaretlenmiş derlemeler, uygulama yüklendiğinde veya güncelleştirilirse indirilmeyecektir. Sınıfı üzerinde yöntemini çağırarak derlemeleri ihtiyacınız olduğunda yükleyebilirsiniz <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> <xref:System.Deployment.Application.ApplicationDeployment> .

 Uydu derlemelerinin isteğe bağlı indirilmesi, istek üzerine diğer derleme türlerinin indirilmekten biraz farklılık gösterir. İçin araçları kullanarak bu senaryonun nasıl etkinleştirileceği hakkında daha fazla bilgi ve kod örnekleri için [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bkz. [Izlenecek yol: ClickOnce dağıtım API 'si Ile Isteğe bağlı uydu derlemelerini indirme](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md).

 Ayrıca, bu senaryoyu ' de etkinleştirebilirsiniz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Ayrıca bkz. [Izlenecek yol: Tasarımcıyı kullanarak ClickOnce dağıtım API 'si Ile isteğe bağlı uydu derlemelerini indirme](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) ve [Tasarımcı kullanarak ClickOnce dağıtım API 'Si Ile uydu derlemelerini indirme](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120)).

## <a name="testing-localized-clickonce-applications-before-deployment"></a>Dağıtımdan önce yerelleştirilmiş ClickOnce uygulamalarını test etme
 Bir uydu derlemesi, yalnızca <xref:System.Threading.Thread.CurrentUICulture%2A> uygulamanın ana iş parçacığının özelliği uydu derlemesinin kültürüne ayarlandıysa Windows Forms bir uygulama için kullanılacaktır. Yerel pazarlardaki müşteriler muhtemelen kültüre uygun varsayılan olarak ayarlanmış bir Windows yerelleştirilmiş sürümünü zaten çalıştırıyor.

 Uygulamanızı müşteriler için kullanılabilir hale gelmeden önce yerelleştirilmiş dağıtımları test etmek için üç seçeneğiniz vardır:

- [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Uygulamanızı, Windows 'un uygun yerelleştirilmiş sürümlerinde çalıştırabilirsiniz.

- <xref:System.Threading.Thread.CurrentUICulture%2A>Özelliğini uygulamanızda programlı olarak ayarlayabilirsiniz. (Yöntemi çağırabilmeniz için önce bu özelliğin ayarlanması gerekir <xref:System.Windows.Forms.Application.Run%2A> .)

## <a name="see-also"></a>Ayrıca bkz.
- [\<assemblyIdentity> dosyalarında](../deployment/assemblyidentity-element-clickonce-deployment.md)
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [Globalize Windows Forms](/dotnet/framework/winforms/advanced/globalizing-windows-forms)