---
title: 'Nasıl yapılır: kod yerelleştirin | Microsoft Docs'
description: Yerelleştirilmiş kaynaklara başvuran bir yöntem olan GetGlobalResourceObject çağrılarıyla sabit kodlanmış dizeleri değiştirerek SharePoint 'teki kodu yerelleştirmeye öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing code [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2cbe38c55b92514954cc3487544fed89d68cc4dc
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304579"
---
# <a name="how-to-localize-code"></a>Nasıl yapılır: kod yerelleştirme
  Yerelleştirilmemiş kod, sabit kodlanmış dize değerlerini kullanır. Kod dizelerini yerelleştirmek için, <xref:System.Web.HttpContext.GetGlobalResourceObject%2A> yerelleştirilmiş kaynaklara başvuran bir yöntem olan çağrılarıyla değiştirin.

## <a name="localize-code"></a>Kodu yerelleştirin

#### <a name="to-localize-code"></a>Kodu yerelleştirmek için

1. **Çözüm Gezgini**, bir proje öğesi için kısayol menüsünü açın ve ardından modül **Ekle**' yi seçin  >  **Module**.

     **Kaynak dosya** şablonunu seçin.

    > [!NOTE]
    > Dağıtım türü özelliğinin kullanılabilir olması için kaynak dosyasını bir SharePoint proje öğesine eklediğinizden emin olun. Bu özellik, bu yordamın ilerleyen kısımlarında gereklidir.

2. Varsayılan dil kaynak dosyasına, bir *. resx* uzantısıyla eklenen bir adı (örneğin, *MyAppResources. resx*) sağlayın.

3. SharePoint proje öğesine ayrı kaynak dosyaları eklemek için 1 ve 2. adımları yineleyin: her bir yerelleştirilmiş dil için bir tane.

     Her yerelleştirilmiş kaynak dosyası için aynı temel adı kullanın, ancak kültür KIMLIĞINI ekleyin. Örneğin, *MyAppResources.de-de. resx* adlı bir Almanya yerelleştirilmiş kaynağını adlandırın.

4. Her kaynak dosyasını açın ve yerelleştirilmiş dizeler ekleyin. Her dosyada aynı dize kimliklerini kullanın.

5. Her bir dosyanın sunucu App_GlobalResources klasörüne dağıtımına yol açmak için her bir kaynak dosyasının **dağıtım türü** özelliğinin değerini **AppGlobalResource** olarak değiştirin.

6. Her bir dosyanın **derleme eylemi** özelliğinin değerini **katıştırılmış kaynak** olarak bırakın.

     Gömülü kaynaklar projenin DLL 'sine derlenir.

7. Kaynak uydu dll 'Lerini oluşturmak için projeyi derleyin.

8. **Paket tasarımcısında**, **Gelişmiş** sekmesini seçin ve ardından uydu derlemesini ekleyin.

9. **Konum** kutusunda, BIR kültür kimliği klasörünü konum yoluna ekleyin, örneğin, *de-de \\ \<Project Item Name>.resources.dll*.

10. Çözümünüz System. Web derlemesine henüz başvurmadığından, buna bir başvuru ekleyin ve kodunuza bir yönerge ekleyin <xref:System.Web> .

11. Kodunuzda Kullanıcı tarafından görülebilen ve Kullanıcı arabirimi metni, hatalar ve ileti metni gibi sabit kodlanmış tüm dizeleri bulun. <xref:System.Web.HttpContext.GetGlobalResourceObject%2A>Aşağıdaki söz dizimini kullanarak bir yönteme çağrı ile değiştirin:

    ```csharp
    HttpContext.GetGlobalResourceObject("Resource File Name", "String ID")
    ```

12. Uygulamayı derlemek ve çalıştırmak için **F5** tuşunu seçin.

13. SharePoint 'te varsayılan değer olan görüntüleme dilini değiştirin.

     Yerelleştirilmiş dizeler uygulamada görüntülenir. Yerelleştirilmiş kaynakları göstermek için SharePoint sunucusunda, kaynak dosyasının kültürüyle eşleşen bir dil paketi yüklü olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerini yerelleştirin](../sharepoint/localizing-sharepoint-solutions.md)
- [Nasıl yapılır: bir özelliği yerelleştirme](../sharepoint/how-to-localize-a-feature.md)
- [Nasıl yapılır: ASPX işaretlemesini yerelleştirme](../sharepoint/how-to-localize-aspx-markup.md)
- [Nasıl yapılır: kaynak dosyası ekleme](../sharepoint/how-to-add-a-resource-file.md)
