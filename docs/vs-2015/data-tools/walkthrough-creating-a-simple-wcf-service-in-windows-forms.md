---
title: "İzlenecek yol: Windows Forms 'de basit bir WCF hizmeti oluşturma | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 366567a13ad23ab19ffd88f19997b92025abe952
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671070"
---
# <a name="walkthrough-creating-a-simple-wcf-service-in-windows-forms"></a>İzlenecek yol: Windows Forms içinde basit bir WCF Hizmeti oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yol, basit bir hizmetin nasıl oluşturulacağını [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] , test yapıldığını ve daha sonra bu uygulamaya nasıl Windows Forms bir uygulamadan erişebileceğini gösterir.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="creating-the-service"></a>Hizmeti Oluşturma

#### <a name="to-create-a-wcf-service"></a>Bir WCF hizmeti oluşturmak için

1. **Dosya** menüsünde, **Yeni** ' nin üzerine gelin ve ardından **Proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, **Visual Basic** veya **Visual C#** düğümünü genişletin ve ardından WCF **hizmet kitaplığı**' **na tıklayın.** Projeyi açmak için **Tamam** ' ı tıklatın.

     ![WCF hizmet kitaplığı projesi](../data-tools/media/wcf1.PNG "wcf1")

    > [!NOTE]
    > Bu, test edilebilir ve erişilebilen bir çalışan hizmet oluşturur. Aşağıdaki iki adım, farklı bir veri türünü kullanmak için varsayılan yöntemi nasıl değiştirebileceğinizi göstermektedir. Gerçek bir uygulamada, hizmete kendi işlevlerinizi de eklemeniz gerekir.

3. ![IService1 dosyası](../data-tools/media/wcf2.png "wcf2")

     **Çözüm Gezgini**, IService1. vb veya IService1.cs öğesine çift tıklayın ve aşağıdaki satırı bulun:

     [!code-csharp[WCFWalkthrough#4](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1_2.cs#4)]
     [!code-vb[WCFWalkthrough#4](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1_2.vb#4)]

     Parametresinin türünü şu şekilde değiştirin `value` `String` :

     [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
     [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

     Yukarıdaki kodda, veya özniteliklerini aklınızda edin `<OperationContract()>` `[OperationContract]` . Bu öznitelikler, hizmet tarafından sunulan herhangi bir yöntem için gereklidir.

4. ![Service1 dosyası](../data-tools/media/wcf3.png "wcf3")

     **Çözüm Gezgini**, Service1. vb veya Service1.cs öğesine çift tıklayın ve aşağıdaki satırı bulun:

     [!code-csharp[WCFWalkthrough#5](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1_2.cs#5)]
     [!code-vb[WCFWalkthrough#5](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1_2.vb#5)]

     Değer parametresinin türünü şu şekilde değiştirin `String` :

     [!code-csharp[WCFWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs#2)]
     [!code-vb[WCFWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb#2)]

## <a name="testing-the-service"></a>Hizmeti test etme

#### <a name="to-test-a-wcf-service"></a>Bir WCF hizmetini test etmek için

1. Hizmeti çalıştırmak için **F5** tuşuna basın. Bir **WCF test istemci** formu görüntülenir ve hizmet yüklenir.

2. **WCF Test istemcisi** formunda, **IService1**altındaki **GetData ()** yöntemine çift tıklayın. **GetData** sekmesi görüntülenir.

     ![GetData&#40;&#41; yöntemi](../data-tools/media/wcf4.png "wcf4")

3. **İstek** kutusunda **değer** alanını ve türünü seçin `Hello` .

     ![Değer alanı](../data-tools/media/wcf5.png "wcf5")

4. **Çağır** düğmesine tıklayın. Bir **güvenlik uyarısı** iletişim kutusu görüntülenirse **Tamam**' a tıklayın. Sonuç, **Yanıt** kutusunda görüntülenecektir.

     ![Yanıt kutusundaki Sonuç](../data-tools/media/wcf6.png "wcf6")

5. **Dosya** menüsünde **Çıkış** ' a tıklayarak test formunu kapatın.

## <a name="accessing-the-service"></a>Hizmete erişme

#### <a name="to-reference-a-wcf-service"></a>Bir WCF hizmetine başvurmak için

1. **Dosya** menüsünde, **Ekle** ' nin üzerine gelin ve ardından **Yeni proje**' ye tıklayın.

2. **Yeni proje** iletişim kutusunda, **Visual Basic** veya **Visual C#** düğümünü genişletin ve **Windows**' u seçin ve ardından **Windows Forms uygulama**' yı seçin. Projeyi açmak için **Tamam** ' ı tıklatın.

     ![Windows Forms uygulama projesi](../data-tools/media/wcf7.png "wcf7")

3. **WindowsApplication1** öğesine sağ tıklayın ve **hizmet başvurusu Ekle**' ye tıklayın. **Hizmet başvurusu Ekle** iletişim kutusu görüntülenir.

4. **Hizmet başvurusu Ekle** Iletişim kutusunda **bul**' a tıklayın.

     ![Hizmet Başvurusu Ekle iletişim kutusu](../data-tools/media/wcf8.png "wcf8")

     **Service1** , **Hizmetler** bölmesinde görüntülenir.

5. Hizmet başvurusunu eklemek için **Tamam** ' ı tıklatın.

#### <a name="to-build-a-client-application"></a>İstemci uygulaması oluşturmak için

1. **Çözüm Gezgini**, zaten açık değilse Windows Form Tasarımcısı açmak için **Form1. vb** veya **Form1.cs** öğesine çift tıklayın.

2. **Araç kutusundan**bir `TextBox` denetimi, `Label` denetimi ve `Button` denetimi form üzerine sürükleyin.

     ![Forma denetim ekleme](../data-tools/media/wcf9.png "wcf9")

3. Öğesine çift tıklayın `Button` ve olay işleyicisine aşağıdaki kodu ekleyin `Click` :

     [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
     [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

4. **Çözüm Gezgini**' de, **WindowsApplication1** ' a sağ tıklayın ve **Başlangıç projesi olarak ayarla**' ya tıklayın.

5. Projeyi çalıştırmak için **F5** tuşuna basın. Biraz metin girin ve düğmeye tıklayın. Etikette "girdiğiniz:" ve girdiğiniz metin görüntülenir.

     ![Sonucu gösteren form](../data-tools/media/wcf10.png "wcf10")

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
