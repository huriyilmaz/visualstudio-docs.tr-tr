---
title: 'Nasıl yapılır: WCF Iş akışı hizmeti uygulaması oluşturma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 12d675ac-27d8-4d86-ba16-6f7688f8c841
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9bf941babd943c6856809a13de847b62745b2056
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72605006"
---
# <a name="how-to-create-a-wcf-workflow-service-application"></a>Nasıl Yapılır: WCF İş Akışı Hizmeti Uygulaması Oluşturma
[!INCLUDE[indigo1](../includes/indigo1-md.md)] iş akışı hizmeti uygulamaları, istemcilerle işlem sınırları arasında iletileri geçen dağıtılmış iletişim hizmetleridir. Hizmet tarafındaki hizmet sözleşmesinin uygulanması, [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] .NET Framework 3,5 ' deki eski iş akışı hizmetlerine benzer şekilde ' de iş akışı etkinlikleri aracılığıyla bildirimli olarak yapılır.

### <a name="to-create-a-wcf-workflow-service-application"></a>Bir WCF iş akışı hizmeti uygulaması oluşturmak için

1. Başlatın [!INCLUDE[vs2010](../includes/vs2010-md.md)] .

2. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve ardından **proje...** öğesini seçin.

     **Yeni proje** iletişim kutusu açılır.

3. **Yüklü şablonlar** bölmesinde, tercih ettiğiniz dile bağlı olarak, **Visual C#** veya **Visual Basic** gruplandırmaları içinden **WCF** veya **iş akışı** ' nı seçin.

4. Orta bölmede, **WCF Iş akışı hizmeti uygulaması**' nı seçin.

5. **Ad** kutusuna projeniz için açıklayıcı bir ad girin ve kolayca tanımlanmasını sağlayın.

6. **Konum** kutusunda, projenizi kaydetmek istediğiniz dizini girin veya git ' e tıklayarak bu dosyayı **gösterin** .

7. **Çözüm** kutusunda, yeni bir çözüm oluşturup **Tamam**' ı seçin.

    > [!NOTE]
    > Mevcut bir çözüme bir iş akışı konsol uygulaması eklemek istiyorsanız, bu çözümü içinde açın [!INCLUDE[vs2010](../includes/vs2010-md.md)] , **Çözüm Gezgini**' de çözüme sağ tıklayın ve **Ekle**, **Yeni proje..** . öğesini seçin. **Yeni proje** iletişim kutusunu açmak için. Bu yordamda yukarıda açıklanan şekilde ilerleyin.

8. Proje şablonu, XAML olarak bir hizmet tanımı oluşturur. , [!INCLUDE[wfd1](../includes/wfd1-md.md)] <xref:System.Activities.Statements.Sequence> Bir dizi ve etkinlik içeren bir etkinlikle Tasarım görünümü açılır <xref:System.ServiceModel.Activities.Receive> <xref:System.ServiceModel.Activities.SendReply> .

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır:](https://msdn.microsoft.com/library/c09b1e99-21b5-4d96-9c04-ec31db3f4436) [iş akışı projesi oluşturma](../workflow-designer/creating-a-workflow-project.md) etkinliği oluşturma