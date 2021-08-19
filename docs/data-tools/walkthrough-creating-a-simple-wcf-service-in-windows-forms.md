---
title: Windows Forms 'de basit bir WCF hizmeti oluşturma
description: bu kılavuzda, Visual Studio ' de bir Windows Communication Foundation (WCF) hizmeti oluşturun, test edin ve bir Windows Forms uygulamasından erişin.
ms.date: 11/04/2016
ms.custom: SEO-VS-2020
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WCF, walkthrough [Visual Studio]
- WCF, Visual Studio tools for
- WCF services
- WCF services, walkthrough
ms.assetid: 5fef1a64-27a4-4f10-aa57-29023e28a2d6
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7ccb7f38e3d459a445b7bb7712e705d1af6f3ada
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122066974"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>izlenecek yol: Windows Forms basit bir WCF hizmeti oluşturma

bu izlenecek yol, basit bir Windows Communication Foundation (WCF) hizmeti oluşturmayı, test etmek ve sonra bu bir Windows Forms uygulamasından erişmeyi gösterir.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-a-service"></a>Hizmet oluşturma

1. Visual Studio'yu açın.

::: moniker range="vs-2017"

2. **dosya** menüsünde **yeni** > **Project**' yi seçin.

3. **yeni Project** iletişim kutusunda, **Visual Basic** veya **Visual C#** düğümünü genişletin ve ardından wcf **hizmet kitaplığı** **' nı** seçin.

4. Projeyi oluşturmak için **Tamam**'a tıklayın.

   ![WCF hizmet kitaplığı projesi](../data-tools/media/wcf1.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Başlangıç penceresinde **Yeni proje oluştur**' u seçin.

3. **Yeni proje oluştur** sayfasındaki arama kutusuna **WCF hizmet kitaplığı** yazın. **WCF hizmet kitaplığı** için C# veya Visual Basic şablonu ' nu seçin ve ardından **ileri**' ye tıklayın.

   ![Visual Studio 2019 ' de yeni WCF hizmet kitaplığı projesi oluştur](media/vs-2019/create-new-wcf-service-library.png)

   > [!TIP]
   > herhangi bir şablon görmüyorsanız, Visual Studio **Windows Communication Foundation** bileşenini yüklemeniz gerekebilir. Visual Studio Yükleyicisi açmak için **daha fazla araç ve özellik yüklemeyi** seçin. **ayrı bileşenler** sekmesini seçin, **geliştirme etkinlikleri**' ne gidin ve ardından **Windows Communication Foundation**' yi seçin. **Değiştir**' e tıklayın.

4. **Yeni projenizi yapılandırın** sayfasında **Oluştur**' a tıklayın.

::: moniker-end

   > [!NOTE]
   > Bu, test edilebilir ve erişilebilen bir çalışan hizmet oluşturur. Aşağıdaki iki adım, farklı bir veri türünü kullanmak için varsayılan yöntemi nasıl değiştirebileceğinizi göstermektedir. Gerçek bir uygulamada, hizmete kendi işlevlerinizi de eklemeniz gerekir.

5. **Çözüm Gezgini**, **IService1. vb** veya **IService1. cs**' ye çift tıklayın.

   ![IService1 dosyası](../data-tools/media/wcf2.png)

   Şu satırı bulun:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1_2.cs" id="Snippet4":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1_2.vb" id="Snippet4":::

   `value`Parametrenin türünü dize olarak değiştirin:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb" id="Snippet1":::

   Yukarıdaki kodda, veya özniteliklerini aklınızda edin `<OperationContract()>` `[OperationContract]` . Bu öznitelikler, hizmet tarafından sunulan herhangi bir yöntem için gereklidir.

6. **Çözüm Gezgini**, **Service1. vb** veya **Service1. cs**' ye çift tıklayın.

   ![Service1 dosyası](../data-tools/media/wcf3.png)

   Şu satırı bulun:

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1_2.vb" id="Snippet5":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1_2.cs" id="Snippet5":::

   `value`Parametrenin türünü dize olarak değiştirin:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs" id="Snippet2":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb" id="Snippet2":::

## <a name="test-the-service"></a>Hizmeti test etme

1. Hizmeti çalıştırmak için **F5** tuşuna basın. Bir **WCF Test istemcisi** formu görünür ve hizmeti yükler.

2. **WCF Test istemcisi** formunda, **IService1** altındaki **GetData ()** yöntemine çift tıklayın. **GetData** sekmesi görüntülenir.

     ![GetData&#40;&#41; yöntemi](../data-tools/media/wcf4.png)

3. **İstek** kutusunda **değer** alanını ve türünü seçin `Hello` .

     ![Değer alanı](../data-tools/media/wcf5.png)

4. **Çağır** düğmesine tıklayın. Bir **güvenlik uyarısı** iletişim kutusu görünürse, **Tamam**' a tıklayın. Sonuç, **Yanıt** kutusunda görüntülenir.

     ![Yanıt kutusundaki Sonuç](../data-tools/media/wcf6.png)

5. **Dosya** menüsünde **Çıkış** ' a tıklayarak test formunu kapatın.

## <a name="access-the-service"></a>Hizmete erişme

### <a name="reference-the-wcf-service"></a>WCF hizmetine başvur

1. **Dosya** menüsünde, **Ekle** ' nin üzerine gelin ve ardından **yeni Project**' ye tıklayın.

2. **yeni Project** iletişim kutusunda, **Visual Basic** veya **Visual C#** düğümünü genişletin, **Windows**' yı seçin ve sonra **Windows Forms uygulama**' yı seçin. Projeyi açmak için **Tamam** ' ı tıklatın.

     ![Windows Forms uygulama projesi](../data-tools/media/wcf7.png)

3. **WindowsApplication1** öğesine sağ tıklayın ve **hizmet başvurusu Ekle**' ye tıklayın. **Hizmet başvurusu Ekle** iletişim kutusu görüntülenir.

4. **Hizmet başvurusu Ekle** Iletişim kutusunda **bul**' a tıklayın.

     ![Hizmet Başvurusu Ekle iletişim kutusu](../data-tools/media/wcf8.png)

     **Service1** , **Hizmetler** bölmesinde görüntülenir.

5. Hizmet başvurusunu eklemek için **Tamam** ' ı tıklatın.

### <a name="build-a-client-application"></a>İstemci uygulaması oluşturma

1. **Çözüm Gezgini**, zaten açık değilse Windows Form Tasarımcısı açmak için **form1. vb** veya **form1. cs** ' ye çift tıklayın.

2. **Araç kutusundan** bir `TextBox` denetimi, `Label` denetimi ve `Button` denetimi form üzerine sürükleyin.

     ![Forma denetim ekleme](../data-tools/media/wcf9.png)

3. Öğesine çift tıklayın `Button` ve olay işleyicisine aşağıdaki kodu ekleyin `Click` :

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb" id="Snippet3":::

4. **Çözüm Gezgini**' de, **WindowsApplication1** ' a sağ tıklayın ve **Başlangıç Project olarak ayarla**' ya tıklayın.

5. Projeyi çalıştırmak için **F5** tuşuna basın. Biraz metin girin ve düğmeye tıklayın. Etiket "girdiğiniz:" görüntüler ve girdiğiniz metni gösterir.

     ![Sonucu gösteren form](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
