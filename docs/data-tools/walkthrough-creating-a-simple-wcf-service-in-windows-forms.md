---
title: Windows Forms'ta basit bir WCF Hizmeti oluşturma
description: Bu kılavuzda, Windows'de bir Windows Communication Foundation (WCF Visual Studio) hizmeti oluşturun, test Windows Forms uygulamasından erişin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631058"
---
# <a name="walkthrough-create-a-simple-wcf-service-in-windows-forms"></a>Adım adım kılavuz: Windows Forms'ta basit bir WCF hizmeti oluşturma

Bu kılavuzda basit bir Windows Communication Foundation (WCF) hizmeti oluşturma, test etmek ve ardından Windows Forms uygulamasından bu hizmete erişmeyi göstereceğiz.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="create-a-service"></a>Hizmet oluşturma

1. Visual Studio'yu açın.

::: moniker range="vs-2017"

2. Dosya menüsünde **Yeni** **dosya'Project.** > 

3. Yeni **Project** iletişim kutusunda, Visual Basic veya  **Visual C# düğümünü** genişletin ve **WCF'yi** ve ardından WCF Hizmet **Kitaplığı'ı seçin.**

4. Projeyi oluşturmak için **Tamam**'a tıklayın.

   ![WCF Hizmet Kitaplığı projesi](../data-tools/media/wcf1.png)

::: moniker-end

::: moniker range=">=vs-2019"

2. Başlangıç penceresinde Yeni proje **oluştur'a tıklayın.**

3. Yeni **proje oluştur sayfasındaki** arama kutusuna wcf hizmet **kitaplığı** yazın. **WCF** Hizmet Kitaplığı için C# veya Visual Basic şablonunu seçin ve ardından Sonraki 'ye **tıklayın.**

   ![Visual Studio 2019'da yeni WCF Hizmet Kitaplığı projesi oluşturma](media/vs-2019/create-new-wcf-service-library.png)

   > [!TIP]
   > Şablon görmüyorsanız, Windows **Communication Foundation** bileşenini yüklemeniz Visual Studio. Daha **fazla araç ve özellik yükle'yi** seçen Visual Studio Yükleyicisi. Bağımsız bileşenler **sekmesini seçin,** Geliştirme etkinlikleri'ne **inin** ve **ardından Communication Foundation'Windows seçin.** **Değiştir'e tıklayın.**

4. Yeni **projenizi yapılandır sayfasında Oluştur'a** **tıklayın.**

::: moniker-end

   > [!NOTE]
   > Bu, test edilebilir ve erişilebilen çalışan bir hizmet oluşturur. Aşağıdaki iki adımda, varsayılan yöntemi farklı bir veri türü kullanmak üzere nasıl değiştirebilirsiniz? Gerçek bir uygulamada, hizmete kendi işlevlerinizi de eklersiniz.

5. **'Çözüm Gezgini** **IService1.vb veya IService1.cs'ye** çift **tıklayın.**

   ![IService1 dosyası](../data-tools/media/wcf2.png)

   Şu satırı bulun:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1_2.cs" id="Snippet4":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1_2.vb" id="Snippet4":::

   Parametresinin türünü `value` dize olarak değiştirme:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs" id="Snippet1":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb" id="Snippet1":::

   Yukarıdaki kodda veya `<OperationContract()>` özniteliklerine `[OperationContract]` dikkat edin. Bu öznitelikler, hizmet tarafından ortaya atfı yapılan tüm yöntemler için gereklidir.

6. Içinde **Çözüm Gezgini** Service1.vb veya **Service1.cs'ye çift tıklayın.** 

   ![Service1 dosyası](../data-tools/media/wcf3.png)

   Şu satırı bulun:

   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1_2.vb" id="Snippet5":::
   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1_2.cs" id="Snippet5":::

   Parametresinin türünü `value` dize olarak değiştirme:

   :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/service1.cs" id="Snippet2":::
   :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/service1.vb" id="Snippet2":::

## <a name="test-the-service"></a>Hizmeti test etme

1. Hizmeti **çalıştırmak için F5** tuşuna basın. Bir **WCF Test İstemcisi** formu görüntülenir ve hizmeti yükler.

2. **WCF Test İstemcisi formunda,** IService1 altındaki **GetData()** **yöntemine çift tıklayın.** **GetData sekmesi** görüntülenir.

     ![GetData&#40;&#41; yöntemi](../data-tools/media/wcf4.png)

3. İstek **kutusuna** Değer alanını seçin **ve** `Hello` yazın.

     ![Değer alanı](../data-tools/media/wcf5.png)

4. Çağır **düğmesine** tıklayın. Bir Güvenlik **Uyarısı iletişim** kutusu görüntülenirse Tamam'a **tıklayın.** Sonuç Yanıt **kutusunda** görüntülenir.

     ![Yanıt kutusunda sonuç](../data-tools/media/wcf6.png)

5. Dosya menüsünde **Çıkış'a** **tıklar** ve test formunu kapatın.

## <a name="access-the-service"></a>Hizmete Erişme

### <a name="reference-the-wcf-service"></a>WCF hizmetine başvuru

1. Dosya menüsünde **Ekle'nin** üzerine **gelin ve yeni** dosya'ya **Project.**

2. Yeni **Project** iletişim kutusunda, **Visual Basic** veya **Visual C# düğümünü** genişletin, Windows'ı seçin ve ardından Windows **Forms Uygulaması'Windows seçin.** Projeyi **açmak** için Tamam'a tıklayın.

     ![Windows Forms Uygulaması projesi](../data-tools/media/wcf7.png)

3. **WindowsApplication1'e sağ tıklayın ve** **Hizmet Başvurusu Ekle.** Hizmet Başvurusu Ekle  iletişim kutusu görüntülenir.

4. Hizmet Başvurusu Ekle **iletişim** kutusunda, Keşfet'e **tıklayın.**

     ![Hizmet Başvurusu Ekle iletişim kutusu](../data-tools/media/wcf8.png)

     **Hizmet1,** Hizmetler **bölmesinde** görüntülenir.

5. Hizmet **başvurularını** eklemek için Tamam'a tıklayın.

### <a name="build-a-client-application"></a>İstemci uygulaması oluşturma

1. Bu **Çözüm Gezgini** **Form1.vb** veya **Form1.cs'ye** çift tıklar ve açık Windows Form Tasarımcısı'nda açılır.

2. Araç **Kutusundan,** bir `TextBox` denetimi, denetimi `Label` ve denetimi `Button` forma sürükleyin.

     ![Forma denetimler ekleme](../data-tools/media/wcf9.png)

3. 'a çift `Button` tıklayın ve olay işleyicisinde aşağıdaki kodu `Click` ekleyin:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb" id="Snippet3":::

4. Içinde **Çözüm Gezgini** **WindowsApplication1'e** sağ tıklayın ve Başlangıç Olarak Ayarla'ya **Project.**

5. Projeyi **çalıştırmak için F5** tuşuna basın. Biraz metin girin ve düğmesine tıklayın. Etikette "Girdiğiniz:" ve girdiğiniz metin görüntülenir.

     ![Sonucu gösteren form](../data-tools/media/wcf10.png)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da Windows Communication Foundation Hizmetleri ve WCF Veri Hizmetleri](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
