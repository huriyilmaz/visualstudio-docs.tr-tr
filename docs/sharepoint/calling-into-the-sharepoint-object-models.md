---
title: SharePoint nesne modellerine çağırma | Microsoft Docs
description: SharePoint araçları uzantılarında kullanabileceğiniz iki farklı nesne modeline nasıl çağrılacağını anlayın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, client object model
- SharePoint development in Visual Studio, server object model
- SharePoint commands [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extensibility features
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 14358b5cc84f63227fd5001731c261002a324492
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99928945"
---
# <a name="call-into-the-sharepoint-object-models"></a>SharePoint nesne modellerine çağrı
  Visual Studio 'da SharePoint araçları için Uzantılar oluşturduğunuzda, belirli görevleri gerçekleştirmek için SharePoint API 'Lerini çağırmanız gerekebilir. Örneğin, SharePoint projeleri için özel bir dağıtım adımı oluşturursanız, çözümleri dağıtmak için bazı görevleri gerçekleştirmek üzere SharePoint API 'Lerini çağırmanız gerekebilir.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] ve [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] SharePoint araçları uzantılarında kullanabileceğiniz iki farklı nesne modeli sağlar: sunucu nesne modeli ve istemci nesne modeli. Her nesne modelinde, SharePoint Araçları uzantıları bağlamında avantajlar ve dezavantajları vardır.

 SharePoint nesne modellerine genel bakış için bkz. [SharePoint araçları uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Uzantı projelerinde istemci nesne modelini kullanma
 SharePoint araçları için bir uzantı geliştirirken, projenizdeki istemci nesne modelini başka bir yönetilen API kümesi gibi kullanabilirsiniz. Projenize istemci nesne modelindeki derlemelere başvurular ekleyebilirsiniz ve doğrudan kodunuzda istemci nesne modelindeki API 'Leri çağırabilirsiniz.

 Ancak, istemci nesne modelinin SharePoint Araçları uzantıları bağlamında iki Sakıncaı vardır:

- İstemci nesne modeli, sunucu nesne modelinin yalnızca bir alt kümesini sağlar. İstemci nesne modelinde gösterilmeyen SharePoint işlevlerini kullanmanız gerekiyorsa, sunucu nesne modelini kullanmanız gerekir.

- SharePoint araçları uzantılarında istemci nesne modelinin kullanılması çoğu durumda çalışmalıdır, ancak istemci nesne modeline yapılan çağrıların beklendiği gibi çalışmamaları durumunda bazı senaryolar yaşayabilirsiniz. İstemci nesne modeli, uzak bir sunucu veya gruptaki SharePoint sitelerine çağrı yapmak için istemci uygulamalarında kullanılmak üzere tasarlanmıştır. Visual Studio 'daki SharePoint araçları, yalnızca geliştirme bilgisayarındaki yerel bir SharePoint yüklemesiyle çalışır. Bu nedenle, istemci nesne modelini bir SharePoint Araçları uzantısında kullandığınızda, yerel bilgisayarda, istemci nesne modelinin kullanılmak üzere tasarlanma biçimi olmayan bir SharePoint sitesine çağrı yapılır.

  Visual Studio 'da SharePoint araçlarının uzantısında İstemci nesne modelinin nasıl kullanılacağını gösteren bir anlatım için bkz. [Izlenecek yol: SharePoint istemci nesne modelini bir Sunucu Gezgini uzantısında çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Uzantı projelerinde sunucu nesne modelini kullanma
 Sunucu nesne modeli, istemci nesne modelinin bir üst kümesidir. Sunucu nesne modelini kullanırken, programlı bir şekilde kullanıma sunan tüm özellikleri kullanabilirsiniz [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] .

 SharePoint Araçları uzantıları sunucu nesne modelinde API 'Leri kullanabilir, ancak doğrudan API 'Leri çağıramaz. Sunucu nesne modeli yalnızca .NET Framework 3,5 ' i hedefleyen 64 bitlik bir işlemden çağrılabilir. Ancak, SharePoint Araçları uzantıları için, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 32 bit Visual Studio işleminde çalıştırmaları gerekir. Bu, SharePoint araçları uzantılarının SharePoint Server nesne modelindeki derlemelere doğrudan başvurmasını önler.

 Sunucu nesne modelini bir SharePoint Araçları uzantısında kullanmak istiyorsanız, API 'yi çağırmak için özel bir *SharePoint komutu* oluşturmanız gerekir. SharePoint komutunu sunucu nesne modeline doğrudan çağırabilmeniz için bir ikincil derlemede tanımlarsınız. Uzantı projenizde, bir nesnenin ExecuteCommand metodunu kullanarak SharePoint komutunu dolaylı olarak çağırabilirsiniz <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> .

 SharePoint komutları oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: SharePoint komutu oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md) ve [nasıl yapılır: SharePoint komutu yürütme](../sharepoint/how-to-execute-a-sharepoint-command.md). SharePoint komutlarının nasıl dağıtılacağı hakkında bilgi için bkz. [Visual Studio 'Da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 SharePoint komutlarının nasıl oluşturulduğunu ve kullanılacağını gösteren izlenecek yollar için bkz. [Izlenecek yol: SharePoint projeleri için özel bir dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) ve [izlenecek yol: Sunucu Gezgini Web bölümlerini görüntülemek için genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>SharePoint komutlarının nasıl yürütüleceğini anlayın
 SharePoint komutlarını tanımlayan derlemeler *vssphost4.exe* adlı 64 bitlik bir ana bilgisayar işlemine yüklenir. SharePoint Araçları uzantısında bir SharePoint komutunu çağırdığınızda, komut 32 bitlik Visual Studio işlemi (*devenv.exe*) yerine *vssphost4.exe* tarafından yürütülür. Kayıt defterindeki değerleri ayarlayarak SharePoint komutlarının nasıl yürütüldüğü hakkında bazı yönlerini denetleyebilirsiniz. Daha fazla bilgi için bkz. [Visual Studio 'Da SharePoint araçları Için hata ayıklama uzantıları](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: SharePoint komutu oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md)
- [Nasıl yapılır: SharePoint komutu yürütme](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [SharePoint Araç uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
