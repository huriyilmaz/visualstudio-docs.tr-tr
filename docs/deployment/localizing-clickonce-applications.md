---
title: ClickOnce Applications | Microsoft Docs
description: Uygulama uygulamalarınızı belirli bir kültüre ClickOnce bir sürüme yerelleştirmenin üç yolu hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: 97756456d192921c2fff4ef9f283a89e775165c1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122051540"
---
# <a name="localize-clickonce-applications"></a>ClickOnce uygulamalarını yerelleştirme
Yerelleştirme, uygulamalarınızı belirli bir kültüre uygun hale uygulama işlemidir. Bu işlem, kullanıcı arabirimi (UI) metnini bölgeye özgü bir dile çevirip doğru tarih ve para birimi biçimlendirmesini kullanmayı, bir formda denetimlerin boyutunu ayarlamayı ve gerekirse denetimleri sağdan sola yansıtmayı içerir.

 Uygulamanıza yerelleştirme, bir veya daha fazla uydu derlemesi oluşturulmasına neden olur. Her derleme belirli bir kültüre özgü kullanıcı arabirimi dizelerini, görüntüleri ve diğer kaynakları içerir. (Uygulamanın ana yürütülebilir dosyası, uygulamanıza varsayılan kültüre uygun dizeleri içerir.)

 Bu konu başlığında, bir uygulamayı diğer kültürler [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] için dağıtmanın üç yolu açıklanmıştır:

- Tüm uydu derlemelerini tek bir dağıtıma dahil eder.

- Her kültür için tek bir uydu derlemesi her biri dahil olacak şekilde bir dağıtım oluşturma.

- Uydu derlemelerini isteğe bağlı olarak indirin.

## <a name="including-all-satellite-assemblies-in-a-deployment"></a>Bir Dağıtıma Tüm Uydu Derlemelerini Dahil
 Birden çok dağıtım [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] yayımlamak yerine, tüm uydu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] derlemelerini içeren tek bir dağıtım yayımlayın.

 Bu yöntem içinde [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] varsayılandır. 'de bu yöntemi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanmak için ek bir iş yapmak zorunda değildir.

 bu yöntemi ile birlikte *MageUI.exe* için, uygulamanıza kültür olarak  bağımsız olarak *MageUI.exe.* Ardından, tüm uydu derlemelerini dağıtımınıza el ile dahil edebilirsiniz. Bu *MageUI.exe,* uygulama bildiriminizin Dosyalar sekmesindeki **Doldurmak** düğmesini kullanarak uydu **derlemelerini** ekleyebilirsiniz.

 Bu yaklaşımın avantajı, tek bir dağıtım oluşturur ve yerelleştirilmiş dağıtım hikayenizi basitleştirmedir. Çalışma zamanında, kullanıcının işletim sisteminin varsayılan kültürüne bağlı olarak uygun uydu derlemesi Windows kullanılır. Bu yaklaşımın bir dezavantajı, uygulama bir istemci bilgisayara her yüklenirken veya güncelleştirildiğinde tüm uydu derlemelerini indirmesidir. Uygulamanıza çok sayıda dize varsa veya müşterileriniz yavaş bir ağ bağlantısına sahipse, bu işlem uygulama güncelleştirmesi sırasında performansı etkileyebilir.

> [!NOTE]
> Bu yaklaşım, uygulamanın denetimlerin yüksekliğini, genişliğini ve konumunu farklı kültürlerde farklı metin dizesi boyutlarına uyum sağlayacak şekilde otomatik olarak ayarlayabileceğini varsayılır. Windows Formlar, formlarınızı, ve denetimlerinin yanı sıra özelliği de dahil olmak üzere kolayca yerelleştirilebilir hale şekilde tasarlamanıza olanak sağlayan <xref:System.Windows.Forms.FlowLayoutPanel> <xref:System.Windows.Forms.TableLayoutPanel> çeşitli denetimler ve teknolojiler <xref:System.Windows.Forms.Control.AutoSize%2A> içerir.  Ayrıca [bkz. AutoSize ve TableLayoutPanel denetimi Windows formlarda yerelleştirme desteği.](/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))

## <a name="generate-one-deployment-for-each-culture"></a>Her kültür için bir dağıtım oluşturma
 Bu dağıtım stratejisinde, birden çok dağıtım oluşturabilirsiniz. Her dağıtımda, yalnızca belirli bir kültür için gereken uydu derlemesini dahil ve dağıtımı bu kültüre özgü olarak işaretlemeniz gerekir.

 'de bu yöntemi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] kullanmak için **Yayımla sekmesindeki** Dili **Yayımla** özelliğini istediğiniz bölgeye ayarlayın. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , seçerek bölge için gereken uydu derlemesini otomatik olarak dahil eder ve diğer tüm uydu derlemelerini dağıtımdan dışlar.

 Aynı şeyi Microsoft'taMageUI.exe *kullanarak* da gerçekleştirebilirsiniz. [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] Uygulama **bildiriminizin** Dosyalar  sekmesindeki Doldurmak düğmesini kullanarak diğer tüm uydu derlemelerini uygulama dizininden dışlar  ve ardından dağıtım bildiriminizin Ad sekmesinde Kültür alanını  *MageUI.exe.* Bu adımlar yalnızca doğru uydu derlemesini dahil etmekle birlikte, dağıtım bildiriminizin öğesinde `language` `assemblyIdentity` özniteliğini ilgili kültüre de ayarlamıştır.

 Uygulamayı yayımlandıktan sonra, bu adımı, uygulamanın desteklediği her ek kültür için tekrarlamanız gerekir. Her uygulama bildirimi farklı bir uydu derlemeye başvuracak ve her dağıtım bildirimi özniteliği için farklı bir değere sahip olduğundan, her zaman farklı bir Web sunucusu dizinine veya dosya paylaşım dizinine `language` yayımlamalısınız.

## <a name="download-satellite-assemblies-on-demand"></a>İsteğe bağlı uydu derlemelerini indirme
 Tüm uydu derlemelerini tek bir dağıtıma dahil etmek için isteğe bağlı indirmeyi kullanarak performansı geliştirebilirsiniz. Bu, derlemeleri isteğe bağlı olarak işaretlemenizi sağlar. Uygulama yüklenirken veya güncelleştirildiğinde işaretlenmiş derlemeler indirilmez. Derlemelere ihtiyacınız olduğunda sınıfında yöntemini <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> çağırarak <xref:System.Deployment.Application.ApplicationDeployment> yükleyebilirsiniz.

 Uydu derlemelerini isteğe bağlı olarak indirmek, isteğe bağlı olarak diğer derleme türlerini indirmekten biraz farklıdır. için araçları kullanarak bu senaryoyu etkinleştirme hakkında daha fazla bilgi ve kod örnekleri için, bkz. [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] [Walkthrough: Downloading Satellite Assemblies on Demand with the ClickOnce API.](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)

 Bu senaryoyu içinde de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] etkinleştirin.  Ayrıca bkz. [Kılavuz:](/previous-versions/visualstudio/visual-studio-2012/ms366788(v=vs.110)) Tasarımcı kullanarak ClickOnce Dağıtım API'si ile Uydu Derlemelerini İndirme veya Gözden Geçirme: Tasarımcı kullanarak ClickOnce Dağıtım API'si ile Uydu Derlemelerini [İndirme.](/previous-versions/visualstudio/visual-studio-2013/ms366788(v=vs.120))

## <a name="testing-localized-clickonce-applications-before-deployment"></a>Yerelleştirilmiş uygulama ClickOnce önce test etme
 Bir uydu derlemesi, Windows Forms uygulaması için yalnızca uygulamanın ana iş parçacığının özelliği uydu derlemenin kültürüne <xref:System.Threading.Thread.CurrentUICulture%2A> ayarlanmışsa kullanılır. Yerel pazarlarda müşteriler büyük olasılıkla kültürleri uygun varsayılana ayarlanmış Windows yerelleştirilmiş bir sürümünü çalıştırmaktadır.

 Yerelleştirilmiş dağıtımları test etmek için, uygulamalarınızı müşteriler için kullanılabilir hale gelmeden önce üç seçeneğiniz vardır:

- Uygulamalarınızı [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uygulamanın uygun yerelleştirilmiş sürümlerinde Windows.

- Özelliği <xref:System.Threading.Thread.CurrentUICulture%2A> uygulamanıza program aracılığıyla kurabilirsiniz. (Bu özellik, yöntemini çağırmadan önce ayar <xref:System.Windows.Forms.Application.Run%2A> gerekir.)

## <a name="see-also"></a>Ayrıca bkz.
- [\<assemblyIdentity> Öğe](../deployment/assemblyidentity-element-clickonce-deployment.md)
- [ClickOnce güvenliği ve dağıtımı](../deployment/clickonce-security-and-deployment.md)
- [Windows formlarını genelleştirme](/dotnet/framework/winforms/advanced/globalizing-windows-forms)