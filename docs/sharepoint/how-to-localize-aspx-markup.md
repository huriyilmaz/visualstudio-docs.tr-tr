---
title: 'Nasıl yapılır: ASPX Işaretlemesini yerelleştirme | Microsoft Docs'
description: Sabit kodlanmış dize değerlerini yerelleştirilmiş kaynaklara başvuran ifadelerle değiştirerek SharePoint 'te ASPX işaretlemesini yerelleştirmeye öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- localizing XML [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1876e06348d60f8a960b352525fd72ad06795101
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931740"
---
# <a name="how-to-localize-aspx-markup"></a>Nasıl yapılır: ASPX işaretlemesini yerelleştirme
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] (. aspx) sayfaları genellikle sabit kodlanmış dize değerlerini kullanır. Bu dizeleri yerelleştirmek için, bunları yerelleştirilmiş kaynaklara başvuran ifadelerle değiştirin.

## <a name="localize-aspx-markup"></a>ASPX işaretlemesini yerelleştirin

#### <a name="to-localize-aspx-markup"></a>ASPX işaretlemesini yerelleştirmek için

1. Ayrı kaynak dosyaları ekleyin: biri varsayılan dil diğeri, her yerelleştirilmiş dil için bir tane.

     Yalnızca biçimlendirmeyi yerelleştirçalışıyorsanız ve kodu değil, bir genel kaynak dosyası proje öğesi ekleyin. Kodu ve biçimlendirmeyi yerelleştirçalışıyorsanız bir kaynak dosyası proje öğesi ekleyin.

    1. Genel kaynak dosyası eklemek için, **Çözüm Gezgini**' de bir SharePoint proje öğesi için kısayol menüsünü açın ve   >  **Yeni öğe** Ekle ' yi seçin. SharePoint **2010** düğümü altında **Genel kaynaklar dosya** şablonunu seçin.

    2. Bir kaynak dosyası eklemek için, **Çözüm Gezgini**' de bir SharePoint proje öğesi için kısayol menüsünü açın ve   >  **Yeni öğe** Ekle ' yi seçin. **Visual Basic** veya **Visual C#** düğümü altında **kaynaklar dosya** şablonunu seçin.

    > [!NOTE]
    > Dağıtım türü özelliğini etkinleştirmek için kaynak dosyalarını bir SharePoint proje öğesine eklediğinizden emin olun. Bu özellik, bu yordamın ilerleyen kısımlarında gereklidir. Çözümünüz bir SharePoint proje öğesi içermiyorsa, boş bir SharePoint projesi ekleyebilir ve varsayılan *Elements.xml* dosyasını kaldırabilirsiniz.

2. Varsayılan dil kaynak dosyasına, bir *. resx* uzantısıyla eklenen bir adı (örneğin, MyAppResources. resx) sağlayın. Her yerelleştirilmiş kaynak dosyası için aynı temel adı kullanın, ancak kültürü ekleyin [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Örneğin, *MyAppResources.de-de. resx* adlı bir Almanya yerelleştirilmiş kaynağını adlandırın.

3. Her kaynak dosyasının **dağıtım türü** özelliğinin değerini, sunucunun App_GlobalResources klasörüne dağıtmalarını sağlamak Için **AppGlobalResource** olarak değiştirin.

4. ASPX biçimlendirmesine ek olarak kodu yerelleştirmek için kaynaklar kullanıyorsanız, her dosyanın **derleme eylemi** özelliğinin değerini **katıştırılmış kaynak** olarak bırakın. Kaynak dosyalarını yalnızca biçimlendirmeyi yerelleştirmek için kullanıyorsanız, isteğe bağlı olarak dosyaların özellik değerini **içeriğe** dönüştürebilirsiniz. Daha fazla bilgi için bkz. [SharePoint çözümlerini yerelleştirin](../sharepoint/localizing-sharepoint-solutions.md).

5. Her bir dosya için aynı dize kimliklerini kullanarak her bir kaynak dosyasını açın ve yerelleştirilmiş dizeler ekleyin.

6. [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]Aspx sayfası veya Denetim biçimlendirmesinde, sabit kodlanmış dizeleri aşağıdaki biçimi kullanan değerlerle değiştirin:

    ```aspx-csharp
    <%$Resources:Resource File Name, String ID%>
    ```

     Örneğin, bir uygulama sayfasında bir etiket denetimi için metni yerelleştirmek üzere şunları değiştirirsiniz:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="Label text"></asp:Label>
    </asp:Content>
    ```

     şöyle değiştirin:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7. Uygulamayı derlemek ve çalıştırmak için **F5** tuşunu seçin.

8. SharePoint 'te varsayılan değer olan görüntüleme dilini değiştirin.

     Yerelleştirilmiş dizeler uygulamada görüntülenir. Yerelleştirilmiş kaynakları göstermek için SharePoint sunucusunda, kaynak dosyasının kültürüyle eşleşen bir dil paketi yüklü olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerini yerelleştirin](../sharepoint/localizing-sharepoint-solutions.md)
- [Nasıl yapılır: bir özelliği yerelleştirme](../sharepoint/how-to-localize-a-feature.md)
- [Nasıl yapılır: kaynak dosyası ekleme](../sharepoint/how-to-add-a-resource-file.md)
- [Nasıl yapılır: kod yerelleştirme](../sharepoint/how-to-localize-code.md)
