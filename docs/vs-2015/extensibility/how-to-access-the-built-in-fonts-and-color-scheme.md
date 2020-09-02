---
title: 'Nasıl yapılır: yerleşik yazı tiplerine ve renk şemasına erişme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, accessing built-in
- font and color control [Visual Studio SDK], categories
- colors, accessing built-in schemes
ms.assetid: 6905845e-e88e-4805-adcf-21da39108ec7
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a43fb3a22ecb2d04542eacf07bf883590868b75b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685316"
---
# <a name="how-to-access-the-built-in-fonts-and-color-scheme"></a>Nasıl Yapılır: Yerleşik Yazı Tipi ve Renk Şemasına Erişme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio tümleşik geliştirme ortamı (IDE), düzenleyici penceresiyle ilişkili bir yazı tipi ve renk şemasına sahiptir. Bu düzene arabirim aracılığıyla erişebilirsiniz <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
 Yerleşik yazı tipi ve renkler şemasını kullanmak için bir VSPackage gerekir:  
  
- Varsayılan yazı tipleri ve renkler hizmeti ile kullanılacak bir kategori tanımlayın.  
  
- Kategoriyi varsayılan yazı tipleri ve renkler sunucusuyla kaydedin.  
  
- IDE 'ye belirli bir pencerenin, ve arabirimlerini kullanarak yerleşik görüntüleme öğelerini ve kategorilerini kullandığını tavsiye edin `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` .  
  
  IDE, ortaya çıkan kategoriyi pencerenin bir tutamacı olarak kullanır. Kategorinin adı, **yazı tipleri ve renkler** özellik sayfasındaki **ayarları göster:** açılan kutusunda görüntülenir.  
  
### <a name="to-define-a-category-using-built-in-fonts-and-colors"></a>Yerleşik yazı tiplerini ve renkleri kullanarak bir kategori tanımlamak için  
  
1. Rastgele bir GUID oluşturun.  
  
    Bu GUID, bir kategoriyi benzersiz bir şekilde tanımlamak için kullanılır<strong>.</strong> Bu kategori, IDE 'nin varsayılan yazı tiplerini ve renk belirtimini yeniden kullanır.  
  
   > [!NOTE]
   > Ya da diğer arabirimlere sahip yazı tipi ve renk verileri alınırken <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> VSPackages, yerleşik bilgilere başvurmak için bu GUID 'yi kullanır.  
  
2. Kategorinin adı VSPackage 'ın Resources (. RC) dosyasının içindeki bir dize tablosuna eklenmelidir, böylece IDE 'de görüntülendiğine göre yerelleştirilebilecek.  
  
    Daha fazla bilgi için bkz. [dize ekleme veya silme](https://msdn.microsoft.com/library/077077b4-0f4b-4633-92d6-60b321164cab).  
  
### <a name="to-register-a-category-using-built-in-fonts-and-colors"></a>Yerleşik yazı tiplerini ve renkleri kullanarak bir kategori kaydetmek için  
  
1. Aşağıdaki konumda Kategori kayıt defteri girişi için özel bir tür oluşturun:  
  
     [HKLM\SOFTWARE\Microsoft \Adim \\ *\<Visual Studio version>* \FontAndColors \\ *\<Category>* ]  
  
     *\<Category>* kategorinin yerelleştirilmemiş adıdır.  
  
2. Kayıt defteri 'ni, hisse senedi yazı tiplerini ve renk şemasını dört değerle birlikte kullanılacak şekilde doldurun:  
  
    |Ad|Tür|Veriler|Description|  
    |----------|----------|----------|-----------------|  
    |Kategori|REG_SZ|GUID|Hisse senedi yazı tipi ve renk düzenini içeren bir kategoriyi tanımlayan rastgele bir GUID.|  
    |Paket|REG_SZ|GUID|{F5E7E71D-1401-11D1-883B-0000F87579D2}<br /><br /> Bu GUID, varsayılan yazı tipi ve renk yapılandırmasını kullanan tüm VSPackages 'ler tarafından kullanılır.|  
    |NameID|REG_DWORD|ID|VSPackage içindeki yerelleştirilebilir kategori adının kaynak KIMLIĞI.|  
    |ToolWindowPackage|REG_SZ|GUID|Arabirimi uygulayan VSPackage GUID 'ı <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .|  
  
3. 
  
### <a name="to-initiate-the-use-of-system-provided-fonts-and-colors"></a>Sistem tarafından belirtilen yazı tiplerinin ve renklerin kullanımını başlatmak için  
  
1. Bir `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer` arabirimin örneğini pencerenin uygulama ve başlatma bir parçası olarak oluşturun.  
  
2. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyCategoryContainer.GetPropertyCategory%2A> `T:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer` Geçerli örneğe karşılık gelen arabirimin bir örneğini almak için yöntemini çağırın <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  
  
3. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextEditorPropertyContainer.SetProperty%2A>İki kez çağırın.  
  
   - `VSEDITPROPID_ViewGeneral_ColorCategory`Bağımsız değişken olarak bir kez çağırın.  
  
   - `VSEDITPROPID_ViewGeneral_FontCategory`Bağımsız değişken olarak bir kez çağırın.  
  
     Bu, varsayılan yazı tipi ve renk hizmetlerini pencerenin bir özelliği olarak ayarlar ve kullanıma sunar.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yerleşik yazı tiplerinin ve renklerin kullanımını başlatır.  
  
```  
CComVariant vt;  
CComQIPtr<IVsTextEditorPropertyCategoryContainer> spPropCatContainer(m_spView);  
if (spPropCatContainer != NULL){  
    CComPtr<IVsTextEditorPropertyContainer> spPropContainer;  
    if (SUCCEEDED(spPropCatContainer->GetPropertyCategory(GUID_EditPropCategory_View_MasterSettings,   
                                                          &spPropContainer))){  
        CComVariant vt;CComVariant VariantGUID(bstrGuidText);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_FontCategory, VariantGUID);  
        spPropContainer->SetProperty(VSEDITPROPID_ViewGeneral_ColorCategory, VariantGUID);  
    }  
}  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yazı tiplerini ve renkleri kullanma](../extensibility/using-fonts-and-colors.md)   
 [Metin renklendirme için yazı tipi ve renk bilgileri alma](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [Depolanan yazı tipine ve renk ayarlarına erişme](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Yazı Tipi ve Renklere Genel Bakış](../extensibility/font-and-color-overview.md)
