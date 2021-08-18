---
title: 'Nasıl yapılır: ASPX Işaretlemesini yerelleştirme | Microsoft Docs'
description: sabit kodlanmış dize değerlerini yerelleştirilmiş kaynaklara başvuran ifadelerle değiştirerek SharePoint ASPX işaretlemesini yerelleştirmeye öğrenin.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: d80157fc2468c5d6fe78ae88cfa0f940917888a8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122084278"
---
# <a name="how-to-localize-aspx-markup"></a>Nasıl yapılır: ASPX işaretlemesini yerelleştirme
  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] (. aspx) sayfaları genellikle sabit kodlanmış dize değerlerini kullanır. Bu dizeleri yerelleştirmek için, bunları yerelleştirilmiş kaynaklara başvuran ifadelerle değiştirin.

## <a name="localize-aspx-markup"></a>ASPX işaretlemesini yerelleştirin

#### <a name="to-localize-aspx-markup"></a>ASPX işaretlemesini yerelleştirmek için

1. Ayrı kaynak dosyaları ekleyin: biri varsayılan dil diğeri, her yerelleştirilmiş dil için bir tane.

     Yalnızca biçimlendirmeyi yerelleştirçalışıyorsanız ve kodu değil, bir genel kaynak dosyası proje öğesi ekleyin. Kodu ve biçimlendirmeyi yerelleştirçalışıyorsanız bir kaynak dosyası proje öğesi ekleyin.

    1. genel kaynak dosyası eklemek için, **Çözüm Gezgini** SharePoint proje öğesi için kısayol menüsünü açın ve ardından   >  **yeni öğe** ekle ' yi seçin. SharePoint **2010** düğümü altında **genel kaynaklar dosya** şablonunu seçin.

    2. bir kaynak dosyası eklemek için, **Çözüm Gezgini** SharePoint proje öğesi için kısayol menüsünü açın ve ardından   >  **yeni öğe** ekle ' yi seçin. **Visual Basic** veya **Visual C#** düğümü altında **kaynaklar dosya** şablonunu seçin.

    > [!NOTE]
    > dağıtım türü özelliğini etkinleştirmek için SharePoint bir proje öğesine kaynak dosyaları eklediğinizden emin olun. Bu özellik, bu yordamın ilerleyen kısımlarında gereklidir. çözümünüz SharePoint proje öğesi içermiyorsa boş bir SharePoint Project ekleyebilir ve varsayılan *Elements.xml* dosyasını kaldırabilirsiniz.

2. Varsayılan dil kaynak dosyasına, bir *. resx* uzantısıyla eklenen bir adı (örneğin, MyAppResources. resx) sağlayın. Her yerelleştirilmiş kaynak dosyası için aynı temel adı kullanın, ancak kültürü ekleyin [!INCLUDE[TLA2#tla_id](../sharepoint/includes/tla2sharptla-id-md.md)] . Örneğin, *MyAppResources.de-de. resx* adlı bir Almanya yerelleştirilmiş kaynağını adlandırın.

3. Her kaynak dosyasının **dağıtım türü** özelliğinin değerini, sunucunun App_GlobalResources klasörüne dağıtmalarını sağlamak Için **AppGlobalResource** olarak değiştirin.

4. ASPX biçimlendirmesine ek olarak kodu yerelleştirmek için kaynaklar kullanıyorsanız, her dosyanın **derleme eylemi** özelliğinin değerini **katıştırılmış kaynak** olarak bırakın. Kaynak dosyalarını yalnızca biçimlendirmeyi yerelleştirmek için kullanıyorsanız, isteğe bağlı olarak dosyaların özellik değerini **içeriğe** dönüştürebilirsiniz. daha fazla bilgi için bkz. [SharePoint çözümlerini yerelleştirin](../sharepoint/localizing-sharepoint-solutions.md).

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

     kullanıcısı

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
    <asp:Label ID="lbl" runat="server" Text="<%$Resources:MyAppResources,String1%>"></asp:Label>
    </asp:Content>
    ```

7. Uygulamayı derlemek ve çalıştırmak için **F5** tuşunu seçin.

8. SharePoint, varsayılan değer olan görüntüleme dilini değiştirin.

     Yerelleştirilmiş dizeler uygulamada görüntülenir. yerelleştirilmiş kaynakları göstermek için, SharePoint sunucuda kaynak dosyanın kültürüyle eşleşen bir dil paketi yüklü olmalıdır.

## <a name="see-also"></a>Ayrıca bkz.
- [SharePoint çözümlerini yerelleştirin](../sharepoint/localizing-sharepoint-solutions.md)
- [Nasıl yapılır: bir özelliği yerelleştirme](../sharepoint/how-to-localize-a-feature.md)
- [Nasıl yapılır: kaynak dosyası ekleme](../sharepoint/how-to-add-a-resource-file.md)
- [Nasıl yapılır: kod yerelleştirme](../sharepoint/how-to-localize-code.md)
