---
title: 'İzlenecek yol: bir uygulama sayfasını bir Iş akışına ekleme | Microsoft Docs'
description: Bu izlenecek yolda, bir SharePoint iş akışı çözümüne bir uygulama sayfası ekleyin. İş akışı kodunu düzeltme. Uygulama sayfasını oluşturun, kodlayın ve test edin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d07b5272a31a0c649e12f353aefaa7c63c335eb5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882667"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>İzlenecek yol: bir uygulama sayfasını bir iş akışına ekleme
  Bu izlenecek yol, bir iş akışından türetilmiş verileri bir iş akışı projesine görüntüleyen bir uygulama sayfasının nasıl ekleneceğini gösterir. BT Kılavuzu [: ilişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)konu başlığı altında açıklanan projede oluşturulur.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Bir ASPX uygulama sayfasını bir SharePoint iş akışı projesine ekleme.

- İş akışı projesinden veri alma ve düzenleme.

- Uygulama sayfasındaki bir tablodaki verileri görüntüleme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- Ve SharePoint 'in desteklenen sürümleri [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] .

- Visual Studio.

- Ayrıca, [Izlenecek yol: ilişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)başlıklı konudaki projeyi de doldurmanız gerekir.

## <a name="amend-the-workflow-code"></a>İş akışı kodunu Düzeltme
 İlk olarak, sonuç sütununun değerini harcama raporu miktarına ayarlamak için iş akışına bir kod satırı ekleyin. Bu değer daha sonra gider raporu Özet hesaplamasında kullanılır.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>İş akışındaki sonuç sütununun değerini ayarlamak için

1. [Ilgili Izlenecek yol: ilişkilendirme ve başlatma formları Ile Iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) başlıklı konudaki tamamlanan projeyi yükleyin [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. *Workflow1.cs* veya *Workflow1. vb* için kodu açın (programlama dilinize bağlı olarak).

3. `createTask1_MethodInvoking`Yönteminin altına aşağıdaki kodu ekleyin:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Uygulama sayfası oluşturma
 Ardından, projeye bir ASPX formu ekleyin. Bu form, gider raporu iş akışı projesinden alınan verileri görüntüler. Bunu yapmak için bir uygulama sayfası eklersiniz. Bir uygulama sayfası, diğer SharePoint sayfalarıyla aynı ana sayfayı kullanır, yani SharePoint sitesindeki diğer sayfalara benzecektir.

#### <a name="to-add-an-application-page-to-the-project"></a>Projeye bir uygulama sayfası eklemek için

1. ExpenseReport projesini seçin ve ardından menü çubuğunda **Proje**  >  **Ekle yeni öğe**' yi seçin.

2. **Şablonlar** bölmesinde, **uygulama sayfası** şablonunu seçin, proje öğesi için varsayılan adı kullanın (**ApplicationPage1. aspx**) ve **Ekle** düğmesini seçin.

3. [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]ApplicationPage1. aspx dosyasında, `PlaceHolderMain` bölümünü aşağıdaki kodla değiştirin:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     Bu kod, tabloya bir başlıkla birlikte bir tablo ekler.

4. Bölümü aşağıdaki ile değiştirerek uygulama sayfasına bir başlık ekleyin `PlaceHolderPageTitleInTitleArea` :

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Uygulama sayfasını kodlayın
 Ardından, gider raporu Özet uygulama sayfasına kod ekleyin. Sayfayı açtığınızda, kod, ayrılan harcama limitini aşan giderler için SharePoint 'teki görev listesini tarar. Raporda her öğe, masrafların toplamı ile birlikte listelenir.

#### <a name="to-code-the-application-page"></a>Uygulama sayfasını kodlayın

1. **ApplicationPage1. aspx** düğümünü seçin ve ardından menü çubuğunda kodu **görüntüle**' yi seçerek  >   uygulama sayfasının arkasındaki kodu görüntüleyin.

2. Sınıfın en üstündeki **using** veya **Import** deyimlerini (programlama diline bağlı olarak) aşağıdaki gibi değiştirin:

    ```vb
    Imports System
    Imports Microsoft.SharePoint
    Imports Microsoft.SharePoint.WebControls
    Imports System.Collections
    Imports System.Data
    Imports System.Web.UI
    Imports System.Web.UI.WebControls
    Imports System.Web.UI.WebControls.WebParts
    Imports System.Drawing
    Imports Microsoft.SharePoint.Navigation
    ```

    ```csharp
    using System;
    using Microsoft.SharePoint;
    using Microsoft.SharePoint.WebControls;
    using System.Collections;
    using System.Data;
    using System.Web.UI;
    using System.Web.UI.WebControls;
    using System.Web.UI.WebControls.WebParts;
    using System.Drawing;
    using Microsoft.SharePoint.Navigation;
    ```

3. `Page_Load` yöntemine aşağıdaki kodu ekleyin:

    ```vb
    Try
        ' Reference the Tasks list on the SharePoint site.
        ' Replace "TestServer" with a valid SharePoint server name.
        Dim site As SPSite = New SPSite("http://TestServer")
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")
        ' string text = "";
        Dim sum As Integer = 0
        Table1.Rows.Clear()
        ' Add table headers.
        Dim hr As TableHeaderRow = New TableHeaderRow
        hr.BackColor = Color.LightBlue
        Dim hc1 As TableHeaderCell = New TableHeaderCell
        Dim hc2 As TableHeaderCell = New TableHeaderCell
        hc1.Text = "Expense Report Name"
        hc2.Text = "Amount Exceeded"
        hr.Cells.Add(hc1)
        hr.Cells.Add(hc2)
        ' Add the TableHeaderRow as the first item
        ' in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr)
        ' Iterate through the tasks in the Task list and collect those
        ' that have values in the "Related Content" and "Outcome" fields
        ' - the fields written to when expense approval is required.
        For Each item As SPListItem In list.Items
            Dim s_relContent As String = ""
            Dim s_outcome As String = ""
            Try
                ' Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related Content")
                s_outcome = item.GetFormattedValue("Outcome")
            Catch erx As System.Exception
                ' Task does not have fields - skip it.
                Continue For
            End Try
            ' Convert amount to an int and keep a running total.
            If (Not String.IsNullOrEmpty(s_relContent) And Not
              String.IsNullOrEmpty(s_outcome)) Then
                sum = (sum + Convert.ToInt32(s_outcome))
                Dim relContent As TableCell = New TableCell
                relContent.Text = s_relContent
                Dim outcome As TableCell = New TableCell
                outcome.Text = ("$" + s_outcome)
                Dim dataRow2 As TableRow = New TableRow
                dataRow2.Cells.Add(relContent)
                dataRow2.Cells.Add(outcome)
                Table1.Rows.Add(dataRow2)
            End If
        Next
        ' Report the sum of the reports in the table footer.
        Dim tfr As TableFooterRow = New TableFooterRow
        tfr.BackColor = Color.LightGreen
        ' Create a TableCell object to contain the
        ' text for the footer.
        Dim ftc1 As TableCell = New TableCell
        Dim ftc2 As TableCell = New TableCell
        ftc1.Text = "TOTAL: "
        ftc2.Text = ("$" + Convert.ToString(sum))
        ' Add the TableCell object to the Cells
        ' collection of the TableFooterRow.
        tfr.Cells.Add(ftc1)
        tfr.Cells.Add(ftc2)
        ' Add the TableFooterRow to the Rows
        ' collection of the table.
        Table1.Rows.Add(tfr)
    Catch errx As Exception
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))
    End Try
    ```

    ```csharp
    try
    {
        // Reference the Tasks list on the SharePoint site.
        // Replace "TestServer" with a valid SharePoint server name.
        SPSite site = new SPSite("http://TestServer");
        SPList list = site.AllWebs[0].Lists["Tasks"];

        // string text = "";
        int sum = 0;

        Table1.Rows.Clear();

        // Add table headers.
        TableHeaderRow hr = new TableHeaderRow();
        hr.BackColor = Color.LightBlue;
        TableHeaderCell hc1 = new TableHeaderCell();
        TableHeaderCell hc2 = new TableHeaderCell();
        hc1.Text = "Expense Report Name";
        hc2.Text = "Amount Exceeded";
        hr.Cells.Add(hc1);
        hr.Cells.Add(hc2);
        // Add the TableHeaderRow as the first item
        // in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr);

        // Iterate through the tasks in the Task list and collect those
        // that have values in the "Related Content" and "Outcome"
        // fields - the fields written to when expense approval is
        // required.
        foreach (SPListItem item in list.Items)
        {
            string s_relContent = "";
            string s_outcome = "";

            try
            {
                // Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related
                  Content");
                s_outcome = item.GetFormattedValue("Outcome");
            }
            catch
            {
                // Task does not have fields - skip it.
                continue;
            }

            if (!String.IsNullOrEmpty(s_relContent) &&
              !String.IsNullOrEmpty(s_outcome))
            {
                // Convert amount to an int and keep a running total.
                sum += Convert.ToInt32(s_outcome);
                TableCell relContent = new TableCell();
                relContent.Text = s_relContent;
                TableCell outcome = new TableCell();
                outcome.Text = "$" + s_outcome;
                TableRow dataRow2 = new TableRow();
                dataRow2.Cells.Add(relContent);
                dataRow2.Cells.Add(outcome);
                Table1.Rows.Add(dataRow2);
            }
        }

        // Report the sum of the reports in the table footer.
           TableFooterRow tfr = new TableFooterRow();
        tfr.BackColor = Color.LightGreen;

        // Create a TableCell object to contain the
        // text for the footer.
        TableCell ftc1 = new TableCell();
        TableCell ftc2 = new TableCell();
        ftc1.Text = "TOTAL: ";
        ftc2.Text = "$" + Convert.ToString(sum);

        // Add the TableCell object to the Cells
        // collection of the TableFooterRow.
        tfr.Cells.Add(ftc1);
        tfr.Cells.Add(ftc2);

        // Add the TableFooterRow to the Rows
        // collection of the table.
        Table1.Rows.Add(tfr);
    }

    catch (Exception errx)
    {
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());
    }
    ```

    > [!WARNING]
    > Koddaki "TestServer" öğesini, SharePoint çalıştıran geçerli bir sunucunun adıyla değiştirdiğinizden emin olun.

## <a name="test-the-application-page"></a>Uygulama sayfasını test etme
 Ardından, uygulama sayfasının gider verilerini doğru şekilde görüntüleyip görüntülemediğini saptayın.

#### <a name="to-test-the-application-page"></a>Uygulama sayfasını sınamak için

1. Çalıştırmak ve projeyi SharePoint 'e dağıtmak için **F5** tuşunu seçin.

2. Giriş düğmesini seçin ve ardından, SharePoint sitesindeki paylaşılan belgeler listesini göstermek için hızlı **Başlangıç** çubuğundaki **paylaşılan belgeler** bağlantısını seçin.

3. Bu örneğe ilişkin gider raporlarını göstermek için, sayfanın üst kısmındaki **LibraryTools** sekmesinden **Belgeler** bağlantısını seçerek ve ardından araç şeridinde **belgeyi karşıya yükle** düğmesini seçerek belgeler listesine bazı yeni belgeler yükleyin.

4. Bazı belgeleri karşıya yükledikten sonra, sayfanın en üstündeki **LibraryTools** sekmesinde bulunan **kitaplık** bağlantısını seçip araç şeridinde **kitaplık ayarları** düğmesini seçerek iş akışını oluşturun.

5. **Belge kitaplığı ayarları** sayfasında, **izinler ve yönetim** bölümünde **iş akışı ayarları** bağlantısını seçin.

6. **Iş akışı ayarları** sayfasında, **iş akışı Ekle** bağlantısını seçin.

7. **Iş akışı Ekle** sayfasında, **ExpenseReport-Workflow1** iş akışını seçin, Iş akışı için **ExpenseTest** gibi bir ad girin ve ardından **İleri** düğmesini seçin.

    İş akışı Ilişkilendirme formu görüntülenir. Gider limiti miktarını raporlamak için bunu kullanın.

8. Ilişkilendirme formunda, **otomatik onay limiti** kutusuna **1000** girin ve sonra **iş akışını ilişkilendir** düğmesini seçin.

9. SharePoint giriş sayfasına geri dönmek için **giriş** düğmesini seçin.

10. Hızlı Başlat çubuğunda **paylaşılan belgeler** bağlantısını seçin.

11. Aşağı açılan bir oku göstermek için karşıya yüklenen belgelerden birini seçin, seçin ve sonra **Iş akışları** öğesini seçin.

12. İş akışı başlatma formunu göstermek için ExpenseTest yanındaki görüntüyü seçin.

13. **Harcama toplamı** metin kutusuna 1000 ' den büyük bir değer girin ve sonra **iş akışını başlat** düğmesini seçin.

     Bildirilen bir masraf, ayrılan gider miktarını aştığında, Görev Listesi bir görev eklenir. **Tamamlanmamış** değeri olan **ExpenseTest** adlı bir sütun, paylaşılan belgeler listesindeki gider raporu öğesine de eklenir.

14. Paylaşılan belgeler listesindeki diğer belgelerle 11-13 adımlarını yineleyin. (Belgelerin tam sayısı önemli değildir.)

15. Aşağıdaki URL 'YI bir Web tarayıcısında açarak gider raporu Özet uygulaması sayfasını görüntüleyin: **http://**<em>systemname</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     Gider raporu Özet sayfasında, ayrılan miktarı, bu miktarı aşan miktarı ve tüm raporların toplam tutarını aşan tüm gider raporları listelenir.

## <a name="next-steps"></a>Sonraki adımlar
 SharePoint uygulama sayfaları hakkında daha fazla bilgi için bkz. [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md).

 Visual Studio 'da Visual Web Tasarımcısı 'nı kullanarak SharePoint sayfası içeriğini nasıl tasarlayacağınızı öğrenmek için aşağıdaki konulardan daha fazla bilgi edinebilirsiniz:

- [SharePoint için Web bölümleri oluşturun](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Web bölümleri veya uygulama sayfaları için yeniden kullanılabilir denetimler oluşturun](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Ayrıca bkz.

- [İzlenecek yol: ilişkilendirme ve başlatma formları ile iş akışı oluşturma](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Nasıl yapılır: uygulama sayfası oluşturma](../sharepoint/how-to-create-an-application-page.md)
- [SharePoint için uygulama sayfaları oluşturma](../sharepoint/creating-application-pages-for-sharepoint.md)
- [SharePoint çözümleri geliştirme](../sharepoint/developing-sharepoint-solutions.md)