---
title: Özellik Sayfaları Ekleme ve Kaldırma | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- property pages, adding
- property pages, project subtypes
- property pages, removing
ms.assetid: 34853412-ab8a-4caa-9601-7d0727b2985d
author: acangialosi
ms.author: anthc
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- vssdk
ms.openlocfilehash: 4c3df3104e48ca0ee972e1a27f2c32fd0661088b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740207"
---
# <a name="add-and-remove-property-pages"></a>Özellik sayfaları ekleme ve kaldırma

Proje Tasarımcısı, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]proje özelliklerini, ayarlarını ve kaynaklarını yönetmek için merkezi bir konum sağlar. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Tümleşik geliştirme ortamında (IDE) tek bir pencere olarak görünür ve soldaki sekmelerden erişilen sağdaki birkaç bölme içerir. Proje Tasarımcısı'ndaki bölmeler (genellikle özellik sayfaları olarak adlandırılır) proje türüne ve dile göre değişir. Proje Tasarımcısı'na **Proje** menüsündeki **Özellikler** komutu ile erişilebilir.

Proje alt türünün Sık sık Proje Tasarımcısı'nda ek özellik sayfaları görüntülemesi gerekir. Benzer şekilde, bazı proje alt türleri yerleşik özellik sayfalarının kaldırılmasını gerektirebilir. Her ikisini de yapmak için, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> proje alt yazınızın arabirimi uygulaması ve yöntemi geçersiz kılması <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> gerekir. Bu yöntemi geçersiz kılarak ve numaralandırma `propId` değerlerinden <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> birini içeren parametre kullanarak proje özelliklerini filtreleyebilir, ekleyebilir veya kaldırabilirsiniz. Örneğin, yapılandırmaya bağımlı özellik sayfalarına bir sayfa eklemeniz gerekebilir. Bunu yapmak için yapılandırmaya bağımlı özellik sayfalarını filtrelemeniz ve ardından varolan listeye yeni bir sayfa eklemeniz gerekir.

## <a name="add-and-remove-property-pages-in-project-designer"></a>Project Designer'da özellik sayfaları ekleme ve kaldırma

### <a name="remove-a-property-page"></a>Özellik sayfasını kaldırma

1. Özellik sayfalarını filtrelemek ve `GetProperty(uint itemId, int propId, out object property)` bir `clsids` liste elde etmek için yöntemi geçersiz kılın.

    ```vb
    Protected Overrides int GetProperty(uint itemId, int propId, out object property)
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer
        'Use propId to filter configuration-independent property pages.
        Select Case propId
            ....
            Case CInt(Fix(__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList))
                'Get a semicolon-delimited list of clsids of the configuration-independent property pages
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))
                   Dim propertyPagesList As String = ((String)[property]).ToUpper(CultureInfo.InvariantCulture)
                'Remove the property page here
                   ....
            ....
        End Select
            ....
        Return MyBase.GetProperty(itemId, propId, [property])
    End Function

    ```

    ```csharp
    protected override int GetProperty(uint itemId, int propId, out object property)
    {
        //Use propId to filter configuration-independent property pages.
        switch (propId)
        {
            . . . .

            case (int)__VSHPROPID2.VSHPROPID_PropertyPagesCLSIDList:
                {
                    //Get a semicolon-delimited list of clsids of the configuration-independent property pages
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));
                    string propertyPagesList = ((string)property).ToUpper(CultureInfo.InvariantCulture);
                    //Remove the property page here
                    . . . .
                }
             . . . .
         }
            . . . .
        return base.GetProperty(itemId, propId, out property);
    }
    ```

2. Etkinlikler **Oluştur** sayfasını elde `clsids` edilen listeden kaldırın.

    ```vb
    Private buildEventsPageGuid As String = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}"
    Private index As Integer = propertyPagesList.IndexOf(buildEventsPageGuid)
    If index <> -1 Then
        ' GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'
        Dim index2 As Integer = index + buildEventsPageGuid.Length + 1
        If index2 >= propertyPagesList.Length Then
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(";"c)
        Else
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2)
        End If
    End If
    'New property value
    property = propertyPagesList
    ```

    ```csharp
    string buildEventsPageGuid = "{1E78F8DB-6C07-4D61-A18F-7514010ABD56}";
    int index = propertyPagesList.IndexOf(buildEventsPageGuid);
    if (index != -1)
    {
        // GUIDs are separated by ';' so if you remove the last GUID, also remove the last ';'
        int index2 = index + buildEventsPageGuid.Length + 1;
        if (index2 >= propertyPagesList.Length)
            propertyPagesList = propertyPagesList.Substring(0, index).TrimEnd(';');
        else
            propertyPagesList = propertyPagesList.Substring(0, index) + propertyPagesList.Substring(index2);
    }
    //New property value
    property = propertyPagesList;
    ```

### <a name="add-a-property-page"></a>Özellik sayfası ekleme

1. Eklemek istediğiniz bir özellik sayfası oluşturun.

    ```vb
    Class DeployPropertyPage
            Inherits Form
            Implements Microsoft.VisualStudio.OLE.Interop.IPropertyPage
        'Summary: Return a stucture describing your property page.
        ....
        Public Sub GetPageInfo(ByVal pPageInfo As Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO())
            Dim info As PROPPAGEINFO = New PROPPAGEINFO()
            info.cb = CUInt(Marshal.SizeOf(GetType(PROPPAGEINFO)))
            info.dwHelpContext = 0
            info.pszDocString = Nothing
            info.pszHelpFile = Nothing
            info.pszTitle = "Deployment" 'Assign tab name
            info.SIZE.cx = Me.Size.Width
            info.SIZE.cy = Me.Size.Height
            If Not pPageInfo Is Nothing AndAlso pPageInfo.Length > 0 Then
                pPageInfo(0) = info
            End If
        End Sub
    End Class
    ```

    ```csharp
    class DeployPropertyPage : Form, Microsoft.VisualStudio.OLE.Interop.IPropertyPage
    {
        . . . .
        //Summary: Return a stucture describing your property page.
        public void GetPageInfo(Microsoft.VisualStudio.OLE.Interop.PROPPAGEINFO[] pPageInfo)
        {
            PROPPAGEINFO info = new PROPPAGEINFO();
            info.cb = (uint)Marshal.SizeOf(typeof(PROPPAGEINFO));
            info.dwHelpContext = 0;
            info.pszDocString = null;
            info.pszHelpFile = null;
            info.pszTitle = "Deployment";  //Assign tab name
            info.SIZE.cx = this.Size.Width;
            info.SIZE.cy = this.Size.Height;
            if (pPageInfo != null && pPageInfo.Length > 0)
                pPageInfo[0] = info;
        }
    }
    ```

2. Yeni özellik sayfanızı kaydedin.

    ```vb
    <MSVSIP.ProvideObject(GetType(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)>
    ```

    ```csharp
    [MSVSIP.ProvideObject(typeof(DeployPropertyPage), RegisterUsing = RegistrationMethod.CodeBase)]
    ```

3. Özellik sayfalarını filtrelemek, bir `GetProperty(uint itemId, int propId, out object property)` `clsids` liste elde etmek ve yeni bir özellik sayfası eklemek için yöntemi geçersiz kılın.

    ```vb
    Protected Overrides Function GetProperty(ByVal itemId As UInteger, ByVal propId As Integer, ByRef [property] As Object) As Integer
        'Use propId to filter configuration-dependent property pages.
        Select Case propId
            ....
            case CInt(Fix(__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList)):
                'Get a semicolon-delimited list of clsids of the configuration-dependent property pages.
                ErrorHandler.ThrowOnFailure(MyBase.GetProperty(itemId, propId, [property]))
                'Add the Deployment property page.
                [property] &= ";"c + GetType(DeployPropertyPage).GUID.ToString("B")
        End Select
            ....
            Return MyBase.GetProperty(itemId, propId, [property])
    End Function
    ```

    ```csharp
    protected override int GetProperty(uint itemId, int propId, out object property)
    {
        //Use propId to filter configuration-dependent property pages.
        switch (propId)
        {
            . . . .
            case (int)__VSHPROPID2.VSHPROPID_CfgPropertyPagesCLSIDList:
                {
                    //Get a semicolon-delimited list of clsids of the configuration-dependent property pages.
                    ErrorHandler.ThrowOnFailure(base.GetProperty(itemId, propId, out property));
                    //Add the Deployment property page.
                    property += ';' + typeof(DeployPropertyPage).GUID.ToString("B");
                }
         }
            . . . .
        return base.GetProperty(itemId, propId, out property);
    }
    ```

## <a name="see-also"></a>Ayrıca bkz.

- [Proje alt türleri](../extensibility/internals/project-subtypes.md)
