---
title: Araç penceresi yapılandırma görüntüleme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, configuring
- tool windows, appearance
ms.assetid: 502a4926-bb83-473e-94e2-8e833c5f8b53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1af78bd58c42cf1312e36621011802e908c9e919
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186389"
---
# <a name="tool-window-display-configuration"></a>Araç Penceresi Ekran Yapılandırması
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPackage bir araç penceresi kaydettiğinde, varsayılan konum, boyut, yerleştirme stili ve diğer görünürlük bilgileri isteğe bağlı değerlerde belirtilir. Araç penceresi kaydı hakkında daha fazla bilgi için bkz [. kayıt defterindeki araç pencereleri](../extensibility/tool-windows-in-the-registry.md)  
  
## <a name="window-display-information"></a>Pencere görüntüleme bilgileri  
 Bir araç penceresinin temel görüntüleme yapılandırması, en fazla altı isteğe bağlı değere depolanır:  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              (Default)       = reg_sz: <Package GUID>Name            = reg_sz: <name of tool window>Float           = reg_sz: <position>Style           = reg_sz: <dock style>Window          = reg_sz: <window GUID>Orientation     = reg_sz: <orientation>DontForceCreate = reg_dword: 0x00000000  
```  
  
|Ad|Tür|Veriler|Açıklama|  
|----------|----------|----------|-----------------|  
|Ad|REG_SZ|"Kısa ad buraya gelecek"|Araç penceresini açıklayan kısa bir ad. Yalnızca kayıt defterindeki başvuru için kullanılır.|  
|Float|REG_SZ|"X1, Y1, X2, Y2"|Dört virgülle ayrılmış değer. X1, Y1 araç penceresinin sol üst köşesinin koordinatı. X2, Y2 sağ alt köşenin koordinatıdır. Tüm değerler ekran koordinatlarına göre yapılır.|  
|Stil|REG_SZ|ÜSTÜNE<br /><br /> Float<br /><br /> Bağlandı<br /><br /> Işleminde<br /><br /> "AlwaysFloat"|Araç penceresinin ilk görüntüleme durumunu belirten bir anahtar sözcük.<br /><br /> "MDI" = MDI penceresiyle yerleştirildi.<br /><br /> "Float" = kayan.<br /><br /> "Linked" = başka bir pencereyle bağlantılı (pencere girişinde belirtilir).<br /><br /> "Sekmeli" = başka bir araç penceresiyle birleştirilir.<br /><br /> "AlwaysFloat" = sabitlenemez.<br /><br /> Daha fazla bilgi için aşağıdaki açıklamalar bölümüne bakın.|  
|Pencere|REG_SZ|*\<GUID>*|Araç penceresinin bağlanacağı veya sekmeli bir pencerenin GUID 'SI. GUID, kendi Windows veya IDE 'deki pencerelerin birine ait olabilir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|Yön|REG_SZ|Tarafta<br /><br /> Right<br /><br /> Yüksek<br /><br /> Aşağıya|Aşağıdaki açıklamalar bölümüne bakın.|  
|DontForceCreate|REG_DWORD|0 veya 1|Bu giriş mevcut olduğunda ve değeri sıfır olmadığında pencere yüklenir, ancak hemen görüntülenmez.|  
  
### <a name="comments"></a>Açıklamalar  
 Yön girişi, başlık çubuğu çift tıklatıldığında araç penceresinin zaman içindeki konumunu tanımlar. Konum, pencere girişinde belirtilen pencereye göre belirlenir. Stil girdisi "bağlandı" olarak ayarlandıysa, yönlendirme girdisi "left", "Right", "top" veya "bottom" olabilir. Stil girişi "Sekmeli" ise, yönlendirme girdisi "left" veya "Right" olabilir ve sekmenin nereye ekleneceğini belirtir. Stil girişi "float" ise, araç penceresi ilk olarak kayar. Başlık çubuğu çift tıklandığında, yön ve pencere girişleri uygulanır ve pencere "Sekmeli" stilini kullanır. Stil girişi "AlwaysFloat" ise araç penceresi sabitlenemez. Stil girişi "MDI" ise, araç penceresi MDI alanına bağlanır ve pencere girişi yok sayılır.  
  
### <a name="example"></a>Örnek  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {A0C5197D-0AC7-4B63-97CD-8872A789D233}\  
              (Default)       = reg_sz: {DA9FB551-C724-11D0-AE1F-00A0C90FFFC3}  
              DontForceCreate = reg_dword: 0x00000000  
              Float           = reg_sz: 100,100,450,300  
              Name            = reg_sz: Bookmarks  
              Orientation     = reg_sz: Left  
              Style           = reg_sz: Tabbed  
              Window          = reg_sz: {34E76E81-EE4A-11D0-00A0C90FFFC3}  
```  
  
## <a name="tool-window-visibility"></a>Araç penceresi görünürlüğü  
 İsteğe bağlı görünürlük alt anahtarındaki değerler bir araç penceresinin görünürlük ayarlarını belirlenir. Değerlerin adları, pencerenin görünürlüğünü gerektiren komutların GUID 'Lerini depolamak için kullanılır. Komut yürütülürse, IDE araç penceresinin oluşturulup görünür hale getirilme garantisi verir.  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        <Version>\  
          ToolWindows\  
            <Tool Window GUID>\  
              Visibility\  
                (Default) = reg_sz:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_dword:  
                <GUID>    = reg_sz:  
```  
  
|Ad|Tür|Veriler|Açıklama|  
|----------|----------|----------|-----------------|  
|(Varsayılan)|REG_SZ|Hiçbiri|Boş bırakın.|  
|*\<GUID>*|REG_DWORD veya REG_SZ|0 veya açıklayıcı bir dize.|İsteğe bağlı. Girdinin adı, görünürlük gerektiren bir komutun GUID 'SI olmalıdır. Değer yalnızca bilgilendirici bir dize tutar. Genellikle değer `reg_dword` 0 olarak ayarlanır.|  
  
### <a name="example"></a>Örnek  
  
```  
HKEY_LOCAL_MACHINE\  
  Software\  
    Microsoft\  
      VisualStudio\  
        8.0Exp\  
          ToolWindows\  
            {EEFA5220-E298-11D0-8F78-00A0C9110057}\  
              Visibility\  
                (Default) = reg_sz:  
                {93694fa0-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
                {9DA22B82-6211-11d2-9561-00600818403B} = reg_dword: 0x00000000  
                {adfc4e66-0397-11d1-9f4e-00a0c911004f} = reg_dword: 0x00000000  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [VSPackage temelleri](../misc/vspackage-essentials.md)
