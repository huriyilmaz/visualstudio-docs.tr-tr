---
title: "İzlenecek yol: ClickOnce dağıtım API 'SI ile Isteğe bağlı uydu derlemelerini Indirme | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, globalization
- localization, Windows Forms
- Windows Forms, localization
- globalization, ClickOnce
- satellite assemblies, ClickOnce
- ClickOnce deployment, on-demand download
- localization, ClickOnce deployment
- ClickOnce deployment, localization
ms.assetid: fdaa553f-a27e-44eb-a4e2-08c122105a87
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a84de037661992d1ee185bea2a70db74dac5e618
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65686349"
---
# <a name="walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api"></a>İzlenecek yol: ClickOnce Dağıtım API'si ile Uydu Derlemelerini İndirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Windows Forms uygulamalar, uydu derlemeleri kullanılarak birden çok kültür için yapılandırılabilir. *Uydu derlemesi* , uygulamanın varsayılan kültürü dışında bir kültür için uygulama kaynakları içeren bir derlemedir.  
  
 [ClickOnce uygulamalarını yerelleştirme](../deployment/localizing-clickonce-applications.md)konusunda anlatıldığı gibi, aynı dağıtımda birden çok kültür için birden çok uydu derlemesi dahil edebilirsiniz [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] . Varsayılan olarak, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Tüm uydu derlemelerini istemci makinesine indirir, ancak tek bir istemci muhtemelen yalnızca bir uydu derlemesi gerektirecektir.  
  
 Bu izlenecek yol, uydu derlemelerinizi isteğe bağlı olarak nasıl işaretleyeceğinizi ve yalnızca geçerli kültür ayarlarına yönelik bir istemci makinesi için gereken derlemeyi nasıl indileceğini gösterir. Aşağıdaki yordam, içinde bulunan araçları kullanır [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] . Ayrıca, bu görevi ' de gerçekleştirebilirsiniz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  Ayrıca bkz. [Izlenecek yol: Tasarımcıyı kullanarak ClickOnce dağıtım API 'si Ile isteğe bağlı uydu derlemelerini indirme](https://msdn.microsoft.com/library/ms366788\(v=vs.110\)) ve [Tasarımcı kullanarak ClickOnce dağıtım API 'Si Ile uydu derlemelerini indirme](https://msdn.microsoft.com/library/ms366788\(v=vs.120\)).  
  
> [!NOTE]
> Test amacıyla, aşağıdaki kod örneği program aracılığıyla kültürü olarak ayarlar `ja-JP` . Üretim ortamı için bu kodu ayarlama hakkında daha fazla bilgi için bu konunun ilerleyen kısımlarında yer alan "sonraki adımlar" bölümüne bakın.  
  
## <a name="prerequisites"></a>Önkoşullar  
 Bu konu başlığında, Visual Studio kullanarak uygulamanıza nasıl yerelleştirilmiş kaynaklar ekleneceğini bildiğiniz varsayılmaktadır. Ayrıntılı yönergeler için bkz. [Izlenecek yol: yerelleştirme Windows Forms](https://msdn.microsoft.com/library/vstudio/y99d1cd3\(v=vs.100\).aspx).  
  
### <a name="to-download-satellite-assemblies-on-demand"></a>Uydu derlemelerini isteğe bağlı olarak indirmek için  
  
1. Uydu derlemelerinin isteğe bağlı olarak indirilmesini sağlamak için uygulamanıza aşağıdaki kodu ekleyin.  
  
     [!code-csharp[ClickOnce.SatelliteAssembliesSDK#1](../snippets/csharp/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/CS/Program.cs#1)]
     [!code-vb[ClickOnce.SatelliteAssembliesSDK#1](../snippets/visualbasic/VS_Snippets_Winforms/ClickOnce.SatelliteAssembliesSDK/VB/Form1.vb#1)]  
  
2. [Resgen.exe (kaynak dosya Oluşturucu)](https://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) veya kullanarak uygulamanız için uydu derlemeleri oluşturun [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
3. MageUI.exe kullanarak, bir uygulama bildirimi oluşturun veya mevcut uygulama bildiriminizi açın. Bu araç hakkında daha fazla bilgi için bkz. [MageUI.exe (bildirim oluşturma ve düzenleme aracı, grafik istemci)](https://msdn.microsoft.com/library/f9e130a6-8117-49c4-839c-c988f641dc14).  
  
4. **Dosyalar** sekmesine tıklayın.  
  
5. **Üç nokta** düğmesine (**...**) tıklayın ve Resgen.exe kullanarak oluşturduğunuz uydu derlemeleri dahil olmak üzere tüm uygulamanızın derlemelerini ve dosyalarını içeren dizini seçin. (Uydu derlemesi *, ısocode\ApplicationName.resources.dll biçiminde* bir ada sahip olur. burada, *ıSOCODE* , RFC 1766 biçiminde bir dil tanımlayıcısıdır.)  
  
6. Dosyaları dağıtımınıza eklemek için **doldur** ' a tıklayın.  
  
7. Her uydu derlemesi için **Isteğe bağlı** onay kutusunu seçin.  
  
8. Her uydu derlemesi için Grup alanını ISO dili tanımlayıcısına ayarlayın. Örneğin, Japonca bir uydu derlemesi için bir indirme grubu adı belirtmeniz gerekir `ja-JP` . Bu, kullanıcının özellik ayarına bağlı olarak, adım 1 ' de eklediğiniz kodu uygun uydu derlemesini indirmek üzere etkinleştirir <xref:System.Threading.Thread.CurrentUICulture%2A> .  
  
## <a name="next-steps"></a>Sonraki Adımlar  
 Bir üretim ortamında, büyük olasılıkla belirli bir değere ayarlanmış olan kod örneğinde satırı kaldırmanız gerekir <xref:System.Threading.Thread.CurrentUICulture%2A> , çünkü istemci makineler varsayılan olarak doğru değere sahip olacaktır. Uygulamanız bir Japonca istemci makinesinde çalıştığında, örneğin, <xref:System.Threading.Thread.CurrentUICulture%2A> `ja-JP` Varsayılan olarak olur. Bu değeri programlı olarak ayarlamak, uygulamanızı dağıtmadan önce uydu derlemelerinizi test etmenin iyi bir yoludur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ClickOnce Uygulamalarını Yerelleştirme](../deployment/localizing-clickonce-applications.md)
