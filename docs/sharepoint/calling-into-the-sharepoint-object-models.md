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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 62303e762206762a1351a2ea267860df4152b319ddf910d2fe866def0712c90a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121315336"
---
# <a name="call-into-the-sharepoint-object-models"></a>SharePoint nesne modellerine çağrı
  Visual Studio SharePoint araçları için uzantılar oluşturduğunuzda, belirli görevleri gerçekleştirmek için SharePoint apı 'leri çağırmanız gerekebilir. örneğin, SharePoint projeleri için özel bir dağıtım adımı oluşturursanız, çözümleri dağıtmak üzere bazı görevleri gerçekleştirmek için SharePoint apı 'leri çağırmanız gerekebilir.

 [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)]ve [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] SharePoint araçları uzantılarında kullanabileceğiniz iki farklı nesne modeli sağlar: sunucu nesne modeli ve istemci nesne modeli. her nesne modelinde SharePoint araçları uzantıları bağlamında avantajlar ve dezavantajları vardır.

 SharePoint nesne modellerine genel bakış için bkz. [SharePoint araçları uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md).

## <a name="use-the-client-object-model-in-extension-projects"></a>Uzantı projelerinde istemci nesne modelini kullanma
 SharePoint araçları için bir uzantı geliştirirken, projenizdeki istemci nesne modelini başka bir yönetilen apı kümesi gibi kullanabilirsiniz. Projenize istemci nesne modelindeki derlemelere başvurular ekleyebilirsiniz ve doğrudan kodunuzda istemci nesne modelindeki API 'Leri çağırabilirsiniz.

 ancak, istemci nesne modelinde SharePoint araçları uzantıları bağlamında iki sakıncalar vardır:

- İstemci nesne modeli, sunucu nesne modelinin yalnızca bir alt kümesini sağlar. istemci nesne modelinde gösterilmeyen SharePoint işlevselliği kullanmanız gerekiyorsa, sunucu nesne modelini kullanmanız gerekir.

- SharePoint araçları uzantılarında istemci nesne modelinin kullanılması çoğu durumda çalışmalıdır, ancak istemci nesne modeline yapılan çağrıların beklendiği gibi çalışmamaları durumunda bazı senaryolar yaşayabilirsiniz. istemci nesne modeli, istemci uygulamalarında, uzak bir sunucu veya gruptaki SharePoint siteleri çağırmak üzere kullanılmak üzere tasarlanmıştır. Visual Studio SharePoint araçları, yalnızca geliştirme bilgisayarındaki yerel bir SharePoint yüklemesiyle çalışır. bu nedenle, istemci nesne modelini bir SharePoint araçları uzantısında kullandığınızda, yerel bilgisayarda, istemci nesne modelinin kullanılmak üzere tasarlanma biçimi olmayan bir SharePoint sitesine çağrı yapılır.

  istemci nesne modelinin Visual Studio SharePoint araçlarının bir uzantısında nasıl kullanılacağını gösteren bir anlatım için bkz. [walkthrough: SharePoint istemci nesne modelini bir Sunucu Gezgini uzantısında çağırma](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md).

## <a name="use-the-server-object-model-in-extension-projects"></a>Uzantı projelerinde sunucu nesne modelini kullanma
 Sunucu nesne modeli, istemci nesne modelinin bir üst kümesidir. Sunucu nesne modelini kullanırken, programlı bir şekilde kullanıma sunan tüm özellikleri kullanabilirsiniz [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] .

 SharePoint araçları uzantıları sunucu nesne modelinde apı 'leri kullanabilir, ancak doğrudan apı 'leri çağıramaz. sunucu nesne modeli yalnızca .NET Framework 3,5 ' i hedefleyen 64 bitlik bir işlemden çağrılabilir. ancak, SharePoint araçları uzantıları şunları gerektirir [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] ve 32 bit Visual Studio işleminde çalışır. bu, SharePoint araçları uzantılarının SharePoint sunucusu nesne modelindeki derlemelere doğrudan başvurmalarını engeller.

 sunucu nesne modelini bir SharePoint araçları uzantısında kullanmak istiyorsanız, apı 'yi çağırmak için özel bir *SharePoint komutu* oluşturmanız gerekir. sunucu nesne modeline doğrudan çağırasağlayan bir ikincil derlemede SharePoint komutunu tanımlarsınız. uzantı projenizde, bir nesnenin executecommand metodunu kullanarak SharePoint komutunu dolaylı olarak çağırabilirsiniz <xref:Microsoft.VisualStudio.SharePoint.ISharePointConnection> .

 SharePoint komutları oluşturma ve kullanma hakkında daha fazla bilgi için bkz. [nasıl yapılır: oluşturma SharePoint komutu](../sharepoint/how-to-create-a-sharepoint-command.md) ve [nasıl yapılır: bir SharePoint komutu yürütme](../sharepoint/how-to-execute-a-sharepoint-command.md). SharePoint komutlarının nasıl dağıtılacağı hakkında bilgi için, bkz. [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).

 SharePoint komutlarının nasıl oluşturulduğunu ve kullanılacağını gösteren izlenecek yollar için bkz. [izlenecek yol: SharePoint projeleri için özel dağıtım adımı oluşturma](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md) ve [izlenecek yol: web bölümlerini görüntülemek için Sunucu Gezgini genişletme](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md).

### <a name="understand-how-sharepoint-commands-are-executed"></a>SharePoint komutlarının nasıl yürütüleceğini anlayın
 SharePoint komutları tanımlayan derlemeler *vssphost4.exe* adlı 64 bitlik bir ana bilgisayar işleminde yüklenir. SharePoint araçları uzantısında bir SharePoint komutu çağırdığınızda, komut 32 bit Visual Studio işlemi (*devenv.exe*) yerine *vssphost4.exe* tarafından yürütülür. kayıt defterindeki değerleri ayarlayarak SharePoint komutlarının nasıl yürütüldüğü hakkında bazı noktaları kontrol edebilirsiniz. daha fazla bilgi için bkz. [Visual Studio SharePoint araçları için hata ayıklama uzantıları](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md).

## <a name="see-also"></a>Ayrıca bkz.
- [nasıl yapılır: SharePoint komutu oluşturma](../sharepoint/how-to-create-a-sharepoint-command.md)
- [nasıl yapılır: SharePoint komutu yürütme](../sharepoint/how-to-execute-a-sharepoint-command.md)
- [SharePoint araçları uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
