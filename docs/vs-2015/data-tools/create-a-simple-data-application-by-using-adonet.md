---
title: ADO.NET kullanarak basit bir veri uygulaması oluşturma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 2222841f-e443-4a3d-8c70-4506aa905193
caps.latest.revision: 46
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b524c9d630f30edd226265ac150ef7ec4f6c60d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651069"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>ADO.NET kullanarak basit veri uygulaması oluşturma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Veritabanındaki verileri işleyen bir uygulama oluşturduğunuzda, bağlantı dizelerini tanımlama, veri ekleme ve saklı yordamları çalıştırma gibi temel görevleri gerçekleştirirsiniz. Bu konuyu izleyerek, Visual C# veya Visual Basic ve ADO.NET kullanarak basit bir Windows Forms "veri üzerinden Forms" uygulamasının içinden bir veritabanıyla nasıl etkileşim kuracağınızı bulabilirsiniz.  Veri kümeleri, LINQ to SQL ve Entity Framework dahil olmak üzere tüm .NET veri teknolojileri, sonuçta bu makalede gösterilenler için çok benzeyen adımları gerçekleştirir.

 Bu makalede, verileri bir veritabanından çok hızlı bir şekilde almanın basit bir yolu gösterilmektedir. Uygulamanızın verileri basit olmayan yollarla değiştirmesi ve veritabanını güncelleştirmesi gerekiyorsa, Kullanıcı arabirimi denetimlerini temel verilerdeki değişikliklerle otomatik olarak eşitlemek için Entity Framework kullanmayı ve veri bağlamayı kullanmayı göz önünde bulundurmanız gerekir.

> [!IMPORTANT]
> Kodu basit tutmak için üretime hazırlanma özel durum işleme içermez.

 **Bu konuda**

- [Örnek veritabanını ayarlama](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)

- [Formları oluşturma ve denetimleri ekleme](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)

- [Bağlantı dizesini depolayın](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)

- [Bağlantı dizesini alma](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)

- [Formların kodunu yazma](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)

- [Uygulamanızı test etme](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)

## <a name="prerequisites"></a>Önkoşullar
 Uygulamayı oluşturmak için şunlar gerekir:

- Visual Studio Community Edition.

- SQL Server Express LocalDB.

- Bir [komut dosyası kullanarak SQL veritabanı oluşturma](../data-tools/create-a-sql-database-by-using-a-script.md)bölümündeki adımları izleyerek oluşturduğunuz küçük örnek veritabanı.

- Ayarladıktan sonra veritabanı için bağlantı dizesi. Bu değeri **SQL Server Nesne Gezgini**açarak, veritabanının kısayol menüsünü açıp **Özellikler**' i seçip **ConnectionString**  özelliğine giderek bulabilirsiniz.

  Bu konu başlığı altında, Visual Studio IDE 'nin temel işlevleriyle ilgili bilgi sahibi olduğunuz ve bu formlara form ekleyebileceğiniz, bu formlara düğme ve diğer denetimleri koyabildiğiniz, bu denetimlerin özelliklerini ayarlayabildiğiniz ve basit olayları kodlayWindows Forms abileceğiniz varsayılmaktadır. Bu görevlerle ilgili deneyimli değilseniz, bu konuya başlamadan önce [Visual C# ile çalışmaya başlama ve Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) tamamlamayı öneririz.

## <a name="set-up-the-sample-database"></a><a name="BKMK_setupthesampledatabase"></a> Örnek veritabanını ayarlama
 Bu izlenecek yol için örnek veritabanı, müşteri ve sipariş tablolarından oluşur. Tablolar başlangıçta veri içermez, ancak oluşturacağınız uygulamayı çalıştırdığınızda veri eklersiniz. Veritabanında Ayrıca beş basit saklı yordam bulunur. [Bir betik kullanarak SQL veritabanı oluşturma](../data-tools/create-a-sql-database-by-using-a-script.md) tabloları, birincil ve yabancı anahtarları, kısıtlamaları ve saklı yordamları oluşturan bir Transact-SQL betiği içerir.

## <a name="create-the-forms-and-add-controls"></a><a name="BKMK_createtheformsandaddcontrols"></a> Formları oluşturma ve denetimleri ekleme

1. Windows Forms bir uygulama için bir proje oluşturun ve bunu SimpleDataApp olarak adlandırın.

    Visual Studio, Form1 adlı boş bir Windows formu dahil olmak üzere projeyi ve birkaç dosyayı oluşturur.

2. Projenize üç form olması için iki Windows formu ekleyin ve ardından aşağıdaki adları verin:

   - Gezinti

   - NewCustomer

   - FillOrCancel

3. Her form için aşağıdaki çizimlerde görüntülenen metin kutularını, düğmeleri ve diğer denetimleri ekleyin. Her denetim için, tabloların açıkladığı özellikleri ayarlayın.

   > [!NOTE]
   > Grup kutusu ve etiket denetimleri ekler, ancak kodda kullanılmaz.

   **Gezinti formu**

   ![Gezinti iletişim kutusu](../data-tools/media/simpleappnav.png "SimpleAppNav")

|Gezinti formu için denetimler|Özellikler|
|--------------------------------------|----------------|
|Düğme|Ad = Btnsayfayadd|
|Düğme|Ad = Btnsayfayfillorcancel|
|Düğme|Ad = btnExit|

 **NewCustomer formu**

 ![Yeni müşteri ekleme ve sipariş yerleştirme](../data-tools/media/simpleappnewcust.png "Simpleappnewmüşt")

|NewCustomer formu için denetimler|Özellikler|
|---------------------------------------|----------------|
|TextBox|Ad = txtCustomerName|
|TextBox|Ad = Txtcustomerıd<br /><br /> ReadOnly = true|
|Düğme|Ad = btnCreateAccount|
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maksimum = 5000<br /><br /> Ad = numOrderAmount|
|'A|Format = Short<br /><br /> Ad = dtpOrderDate|
|Düğme|Ad = btnPlaceOrder|
|Düğme|Ad = btnAddAnotherAccount|
|Düğme|Ad = btnaddbitiri|

 **FillOrCancel formu**

 ![siparişleri doldur veya iptal etme](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")

|FillOrCancel formu için denetimler|Özellikler|
|----------------------------------------|----------------|
|TextBox|Ad = txtOrderID|
|Düğme|Ad = Btnfindbyorderıd|
|'A|Format = Short<br /><br /> Ad = dtpFillDate|
|DataGridView|Ad = dgvCustomerOrders<br /><br /> ReadOnly = true<br /><br /> RowHeadersVisible = false|
|Düğme|Ad = btnCancelOrder|
|Düğme|Ad = btnFillOrder|
|Düğme|Ad = Btnsonlandırsupdates|

## <a name="store-the-connection-string"></a><a name="BKMK_storetheconnectionstring"></a> Bağlantı dizesini depolayın
 Uygulamanız veritabanına bir bağlantı açmaya çalıştığında, uygulamanızın bağlantı dizesine erişimi olması gerekir. Dizeyi her bir forma el ile girmekten kaçınmak için, dizeyi projenizdeki uygulama yapılandırma dosyasında depolayın ve yöntemi uygulamanızdaki herhangi bir formdan çağrıldığında dizeyi döndüren bir yöntem oluşturun.

 Bağlantı dizesini veritabanına sağ tıklayıp **Özellikler**' i seçip ConnectionString özelliğini bularak **SQL Server Nesne Gezgini** bulabilirsiniz. Dizeyi seçmek için CTRL + A tuşlarını kullanın.

1. **Çözüm Gezgini**, projenin altındaki **Özellikler** düğümünü seçin ve ardından **ayarlar. ayarlar**' ı seçin.

2. **Ad** sütununda, girin `connString` .

3. **Tür** listesinde **(bağlantı dizesi)** öğesini seçin.

4. **Kapsam** listesinde, **uygulama**' yı seçin.

5. **Değer** sütununda, Bağlantı dizenizi (dış tırnak işaretleri olmadan) girin ve ardından değişikliklerinizi kaydedin.

> [!NOTE]
> Gerçek bir uygulamada bağlantı dizesini [bağlantı dizeleri ve yapılandırma dosyalarında](https://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8)açıklandığı gibi güvenli bir şekilde depolamanız gerekir.

## <a name="retrieve-the-connection-string"></a><a name="BKMK_retrievetheconnectionstring"></a> Bağlantı dizesini alma

1. Menü çubuğunda, **Proje**  >  **Başvuru Ekle**' yi seçin ve ardından System.Configuration.dll bir başvuru ekleyin.

2. **Project**  >  Projenize bir sınıf dosyası eklemek için menü çubuğunda Proje**Ekle sınıf** ' ı seçin ve ardından dosyayı adlandırın `Utility` .

     Visual Studio dosyayı oluşturur ve **Çözüm Gezgini**görüntüler.

3. Yardımcı program dosyasında, yer tutucu kodunu aşağıdaki kodla değiştirin. Kodun bölümlerini tanımlayan numaralandırılmış yorumlara (Util ile ön ek) dikkat edin. Kodu izleyen tablo, anahtar noktalarını çağırır.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Linq;
    using System.Text;
    using System.Threading.Tasks;
    //Util-1 More namespaces.
    using System.Configuration;

    namespace SimpleDataApp
    {
        internal class Utility
        {

            //Get the connection string from App config file.
            internal static string GetConnectionString()
            {
                //Util-2 Assume failure.
                string returnValue = null;

                //Util-3 Look for the name in the connectionStrings section.
                ConnectionStringSettings settings =
                ConfigurationManager.ConnectionStrings["SimpleDataApp.Properties.Settings.connString"];

                //If found, return the connection string.
                if (settings != null)
                    returnValue = settings.ConnectionString;

                return returnValue;
            }
        }
    }
    ```

    ```vb
    Imports System
    Imports System.Collections.Generic
    Imports System.Linq
    Imports System.Text
    Imports System.Threading.Tasks
    ' Util-1 More namespaces.
    Imports System.Configuration

    Namespace SimpleDataApp
        Friend Class Utility

            ' Get connection string from App config file.
            Friend Shared Function GetConnectionString() As String

                ' Util-2 Assume failure.
                Dim returnValue As String = Nothing

                ' Util-3 Look for the name in the connectionStrings section.
                Dim settings As ConnectionStringSettings = ConfigurationManager.ConnectionStrings("SimpleDataApp.My.MySettings.connString")

                ' If found, return the connection string.
                If settings IsNot Nothing Then
                    returnValue = settings.ConnectionString
                End If

                Return returnValue
            End Function
        End Class
    End Namespace
    ```

    |Yorum|Description|
    |-------------|-----------------|
    |Util-1|`System.Configuration`Ad alanını ekleyin.|
    |Util-2|Bir değişken tanımlayın, `returnValue` ve `null` (C#) veya `Nothing` (Visual Basic) olarak başlatın.|
    |Util-3|`connString` **Özellikler** penceresinde bağlantı dizesinin adı olarak girmiş olsanız bile, `"SimpleDataApp.Properties.Settings.connString"` kodda (C#) veya `"SimpleDataApp.My.MySettings.connString"` (Visual Basic) öğesini belirtmeniz gerekir.|

## <a name="write-the-code-for-the-forms"></a><a name="BKMK_writethecodefortheforms"></a> Formların kodunu yazma
 Bu bölümde, her bir formun ne yaptığı hakkında kısa bir genel bakış yer almaktadır ve formları oluşturan kod gösterilmektedir. Numaralandırılmış açıklamalar kodun bölümlerini belirler.

### <a name="navigation-form"></a>Gezinti formu
 Uygulamayı çalıştırdığınızda gezinti formu açılır. **Hesap Ekle** düğmesi NewCustomer formunu açar. **Siparişleri doldur veya iptal et** düğmesi FillOrCancel formunu açar. **Çıkış** düğmesi uygulamayı kapatır.

#### <a name="make-the-navigation-form-the-startup-form"></a>Gezinti formunu başlangıç formu haline getirme
 C# kullanıyorsanız, **Çözüm Gezgini**' de program.cs açın ve ardından `Application.Run` satırı bu şekilde değiştirin: `Application.Run(new Navigation());`

 Visual Basic kullanıyorsanız, **Çözüm Gezgini**' de **Özellikler** penceresini açın, **uygulama** sekmesini seçin ve ardından **başlangıç formu** listesinden **simpledataapp. Navigation** öğesini seçin.

#### <a name="create-event-handlers"></a>Olay işleyicileri oluşturma
 Boş olay işleyici yöntemleri oluşturmak için formdaki üç düğmeye çift tıklayın.

#### <a name="create-code-for-navigation"></a>Gezinti için kod oluştur
 Gezinti formunda, mevcut kodu aşağıdaki kodla değiştirin.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;

namespace SimpleDataApp
{
    public partial class Navigation : Form
    {
        public Navigation()
        {
            InitializeComponent();
        }

        //Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.
        private void btnGoToAdd_Click(object sender, EventArgs e)
        {
            Form frm = new NewCustomer();
            frm.Show();
        }

        //Open the FillorCancel form as a dialog box.
        private void btnGoToFillOrCancel_Click(object sender, EventArgs e)
        {
            Form frm = new FillOrCancel();
            frm.ShowDialog();
        }

        //Close the application, not just the Navigation form.
        private void btnExit_Click(object sender, EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms

Namespace SimpleDataApp
    Partial Public Class Navigation
        Inherits Form
        Public Sub New()
            InitializeComponent()
        End Sub

        ' Open the NewCustomer form as a dialog box, which will return focus to the calling form when it closes.
        Private Sub btnGoToAdd_Click() Handles btnGoToAdd.Click
            Dim frm As Form = New NewCustomer()
            frm.Show()
        End Sub

        ' Open the FillorCancel form as a dialog box.
        Private Sub btnGoToFillOrCancel_Click() Handles btnGoToFillOrCancel.Click
            Dim frm As Form = New FillOrCancel()
            frm.ShowDialog()
        End Sub

        ' Close the application, not just the Navigation form.
        Private Sub btnExit_Click() Handles btnExit.Click
            Me.Close()
        End Sub
    End Class
End Namespace

```

### <a name="newcustomer-form"></a>NewCustomer formu
 Bir müşteri adı girip **Hesap oluştur** düğmesini seçtiğinizde, NewCustomer formu bir müşteri hesabı oluşturur ve SQL Server yeni hesap numarası olarak bir kimlik değeri döndürür. Daha sonra bir tutar ve sipariş tarihi belirtip **siparişi yerleştir** düğmesini seçerek yeni hesap için bir sipariş yerleştirebilirsiniz.

#### <a name="create-event-handlers"></a>Olay işleyicileri oluşturma
 Formdaki her düğme için boş bir tıklama olayı işleyicisi oluşturun.

#### <a name="create-code-for-newcustomer"></a>NewCustomer için kod oluştur
 NewCustomer formuna aşağıdaki kodu ekleyin. Koddan sonra numaralandırılmış açıklamaları ve tabloyu kullanarak her kod bloğunu adım adım yapın.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
//NC-1 More namespaces.
using System.Data.SqlClient;
using System.Configuration;

namespace SimpleDataApp
{
    public partial class NewCustomer : Form
    {
        //NC-2 Storage for IDENTITY values returned from database.
        private int parsedCustomerID;
        private int orderID;

        //NC-3 Specify a connection string.
        string connstr = SimpleDataApp.Utility.GetConnectionString();

        public NewCustomer()
        {
            InitializeComponent();
        }

        //NC-4 Create account.
        private void btnCreateAccount_Click(object sender, EventArgs e)
        {
            //NC-5 Set up and run stored procedure only if Customer Name is present.
            if (isCustomerName())
            {

                //NC-6 Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //NC-7 Create a SqlCommand, and identify it as a stored procedure.
                SqlCommand cmdNewCustomer = new SqlCommand("Sales.uspNewCustomer", conn);
                cmdNewCustomer.CommandType = CommandType.StoredProcedure;

                //NC-8 Add input parameter from the stored procedure and specify what to use as its value.
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerName", SqlDbType.NVarChar, 40));
                cmdNewCustomer.Parameters["@CustomerName"].Value = txtCustomerName.Text;

                //NC-9 Add output parameter.
                cmdNewCustomer.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));
                cmdNewCustomer.Parameters["@CustomerID"].Direction = ParameterDirection.Output;

                //NC-10 try-catch-finally
                try
                {
                    //NC-11 Open the connection.
                    conn.Open();

                    //NC-12 Run the stored procedure.
                    cmdNewCustomer.ExecuteNonQuery();

                    //NC-13 Customer ID is an IDENTITY value from the database.
                    this.parsedCustomerID = (int)cmdNewCustomer.Parameters["@CustomerID"].Value;
                    this.txtCustomerID.Text = Convert.ToString(parsedCustomerID);

                }
                catch
                {
                    //NC-14 A simple catch.

                    MessageBox.Show("Customer ID was not returned. Account could not be created.");
                }
                finally
                {
                    //NC-15 Close the connection.
                    conn.Close();
                }
            }
        }

        //NC-16 Verify that Customer Name is present.
        private bool isCustomerName()
        {
            if (txtCustomerName.Text == "")
            {
                MessageBox.Show("Please enter a name.");
                return false;
            }
            else
            {
                return true;
            }
        }

        //NC-17 Place order.
        private void btnPlaceOrder_Click(object sender, EventArgs e)
        {
            //NC-18 Set up and run stored procedure only if required input is present.
            if (isPlaceOrderReady())
            {
                // Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //NC-19 Create SqlCommand and identify it as a stored procedure.
                SqlCommand cmdNewOrder = new SqlCommand("Sales.uspPlaceNewOrder", conn);
                cmdNewOrder.CommandType = CommandType.StoredProcedure;

                //NC-20 @CustomerID, which was an output parameter from uspNewCustomer.
                cmdNewOrder.Parameters.Add(new SqlParameter("@CustomerID", SqlDbType.Int));
                cmdNewOrder.Parameters["@CustomerID"].Value = this.parsedCustomerID;

                //NC-21 @OrderDate.
                cmdNewOrder.Parameters.Add(new SqlParameter("@OrderDate", SqlDbType.DateTime, 8));
                cmdNewOrder.Parameters["@OrderDate"].Value = dtpOrderDate.Value;

                //NC-22 @Amount.
                cmdNewOrder.Parameters.Add(new SqlParameter("@Amount", SqlDbType.Int));
                cmdNewOrder.Parameters["@Amount"].Value = numOrderAmount.Value;

                //NC-23 @Status. For a new order, the status is always O (open).
                cmdNewOrder.Parameters.Add(new SqlParameter("@Status", SqlDbType.Char, 1));
                cmdNewOrder.Parameters["@Status"].Value = "O";

                //NC-24 Add return value for stored procedure, which is orderID.
                cmdNewOrder.Parameters.Add(new SqlParameter("@RC", SqlDbType.Int));
                cmdNewOrder.Parameters["@RC"].Direction = ParameterDirection.ReturnValue;

                //try-catch-finally
                try
                {
                    //Open connection.
                    conn.Open();

                    //Run the stored procedure.
                    cmdNewOrder.ExecuteNonQuery();

                    //NC-25 Display the order number.
                    this.orderID = (int)cmdNewOrder.Parameters["@RC"].Value;
                    MessageBox.Show("Order number " + this.orderID + " has been submitted.");
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("Order could not be placed.");
                }
                finally
                {
                    //Close connection.
                    conn.Close();
                }
            }
        }

        //NC-26 Verify that order data is ready.
        private bool isPlaceOrderReady()
        {
            // Verify that CustomerID is present.
            if (txtCustomerID.Text == "")
            {
                MessageBox.Show("Please create customer account before placing order.");
                return false;
            }

            // Verify that Amount isn't 0.
            else if ((numOrderAmount.Value < 1))
            {
                MessageBox.Show("Please specify an order amount.");
                return false;
            }
            else
            {
                // Order can be submitted.
                return true;
            }
        }

        //NC-27 Reset the form for another new account.
        private void btnAddAnotherAccount_Click(object sender, EventArgs e)
        {
            this.ClearForm();
        }

        //NC-28 Clear values from controls.
        private void ClearForm()
        {
            txtCustomerName.Clear();
            txtCustomerID.Clear();
            dtpOrderDate.Value = DateTime.Now;
            numOrderAmount.Value = 0;
            this.parsedCustomerID = 0;
        }

        //NC-29 Close the form.
        private void btnAddFinish_Click(object sender, EventArgs e)
        {
            this.Close();
        }

    }
}

```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms
' NC-1 More namespaces.
Imports System.Data.SqlClient
Imports System.Configuration

Namespace SimpleDataApp
    Partial Public Class NewCustomer
        Inherits Form

        ' NC-2 Storage for IDENTITY values returned from database.
        Private parsedCustomerID As Integer
        Private orderID As Integer

        ' NC-3 Specify a connection string.
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()

        Public Sub New()
            InitializeComponent()
        End Sub

        ' NC-4 Create account.
        Private Sub btnCreateAccount_Click() Handles btnCreateAccount.Click

            ' NC-5 Set up and run stored procedure only if Customer Name is present.
            If isCustomerName() Then

                ' NC-6 Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' NC-7 Create a SqlCommand, and identify it as a stored procedure.
                Dim cmdNewCustomer As New SqlCommand("Sales.uspNewCustomer", conn)
                cmdNewCustomer.CommandType = CommandType.StoredProcedure

                ' NC-8 Add input parameter from the stored procedure and specify what to use as its value.
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerName", SqlDbType.NVarChar, 40))
                cmdNewCustomer.Parameters("@CustomerName").Value = txtCustomerName.Text

                ' NC-9 Add output parameter.
                cmdNewCustomer.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))
                cmdNewCustomer.Parameters("@CustomerID").Direction = ParameterDirection.Output

                ' NC-10 try-catch-finally
                Try
                    ' NC-11 Open the connection.
                    conn.Open()

                    ' NC-12 Run the stored procedure.
                    cmdNewCustomer.ExecuteNonQuery()

                    ' NC-13 Customer ID is an IDENTITY value from the database.
                    Me.parsedCustomerID = CInt(cmdNewCustomer.Parameters("@CustomerID").Value)
                    Me.txtCustomerID.Text = Convert.ToString(parsedCustomerID)

                Catch
                    ' NC-14 A simple catch.
                    MessageBox.Show("Customer ID was not returned. Account could not be created.")
                Finally
                    ' NC-15 Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' NC-16 Verify that Customer Name is present.
        Private Function isCustomerName() As Boolean
            If txtCustomerName.Text = "" Then
                MessageBox.Show("Please enter a name.")
                Return False
            Else
                Return True
            End If
        End Function

        ' NC-17 Place order.
        Private Sub btnPlaceOrder_Click() Handles btnPlaceOrder.Click

            ' NC-18 Set up and run stored procedure only if necessary input is present.
            If isPlaceOrderReady() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' NC-19 Create SqlCommand and identify it as a stored procedure.
                Dim cmdNewOrder As New SqlCommand("Sales.uspPlaceNewOrder", conn)
                cmdNewOrder.CommandType = CommandType.StoredProcedure

                ' NC-20 @CustomerID, which was an output parameter from uspNewCustomer.
                cmdNewOrder.Parameters.Add(New SqlParameter("@CustomerID", SqlDbType.Int))
                cmdNewOrder.Parameters("@CustomerID").Value = Me.parsedCustomerID

                ' NC-21 @OrderDate.
                cmdNewOrder.Parameters.Add(New SqlParameter("@OrderDate", SqlDbType.DateTime, 8))
                cmdNewOrder.Parameters("@OrderDate").Value = dtpOrderDate.Value

                ' NC-22 @Amount.
                cmdNewOrder.Parameters.Add(New SqlParameter("@Amount", SqlDbType.Int))
                cmdNewOrder.Parameters("@Amount").Value = numOrderAmount.Value

                ' NC-23 @Status. For a new order, the status is always O (open).
                cmdNewOrder.Parameters.Add(New SqlParameter("@Status", SqlDbType.[Char], 1))
                cmdNewOrder.Parameters("@Status").Value = "O"

                ' NC-24 Add return value for stored procedure, which is orderID.
                cmdNewOrder.Parameters.Add(New SqlParameter("@RC", SqlDbType.Int))
                cmdNewOrder.Parameters("@RC").Direction = ParameterDirection.ReturnValue

                ' try-catch-finally
                Try
                    ' Open connection.
                    conn.Open()

                    ' Run the stored procedure.
                    cmdNewOrder.ExecuteNonQuery()

                    ' NC-25 Display the order number.
                    Me.orderID = CInt(cmdNewOrder.Parameters("@RC").Value)
                    MessageBox.Show("Order number " & (Me.orderID).ToString & " has been submitted.")

                Catch
                    ' A simple catch.
                    MessageBox.Show("Order could  not be placed.")

                Finally
                    ' Close connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' NC-26 Verify that order data is ready.
        Private Function isPlaceOrderReady() As Boolean

            ' Verify that CustomerID is present.
            If txtCustomerID.Text = "" Then
                MessageBox.Show("Please create customer account before placing order.")
                Return False

                ' Verify that Amount isn't 0.
            ElseIf (numOrderAmount.Value < 1) Then

                MessageBox.Show("Please specify an order amount.")
                Return False
            Else
                ' Order can be submitted.
                Return True
            End If
        End Function

        ' NC-27 Reset the form for another new account.
        Private Sub btnAddAnotherAccount_Click() Handles btnAddAnotherAccount.Click
            Me.ClearForm()
        End Sub

        ' NC-28 Clear values from controls.
        Private Sub ClearForm()
            txtCustomerName.Clear()
            txtCustomerID.Clear()
            dtpOrderDate.Value = DateTime.Now
            numOrderAmount.Value = 0
            Me.parsedCustomerID = 0
        End Sub

        ' NC-29 Close the form.
        Private Sub btnAddFinish_Click() Handles btnAddFinish.Click
            Me.Close()
        End Sub

    End Class
End Namespace
```

|Yorum|Description|
|-------------|-----------------|
|NC-1|`System.Data.SqlClient` `System.Configuration` Ad alanları listesine ve ekleyin.|
|NC-2|`parsedCustomerID` `orderID` Daha sonra kullanacağınız ve değişkenlerini bildirin.|
|NC-3|`GetConnectionString`Uygulama yapılandırma dosyasından bağlantı dizesini almak için yöntemini çağırın ve değeri `connstr` dize değişkeninde depolayın.|
|NC-4|Düğme için Click olay işleyicisine kod ekleyin `btnCreateAccount` .|
|NC-5|Çağrıyı `isCustomerName` Click olay kodu etrafında sarmalayın, böylece `uspNewCustomer` yalnızca bir müşteri adı mevcutsa çalışır.|
|NC-6|Bir `SqlConnection` nesne ( `conn` ) oluşturun ve içinde bağlantı dizesini geçirin `connstr` .|
|NC-7|Bir `SqlCommand` nesne oluşturun, `cmdNewCustomer` .<br /><br /> - `Sales.uspNewCustomer` Çalıştırılacak saklı yordam olarak belirtin.<br />- `CommandType` Komutun saklı yordam olduğunu belirtmek için özelliğini kullanın.|
|NC-8|`@CustomerName`Saklı yordamdan giriş parametresini ekleyin.<br /><br /> -Parametreyi `Parameters` koleksiyona ekleyin.<br />- `SqlDbType` Parametre türünü nvarchar (40) olarak belirtmek için numaralandırmayı kullanın.<br />- `txtCustomerName.Text` Kaynak olarak belirtin.|
|NC-9|Saklı yordamdan çıkış parametresini ekleyin.<br /><br /> -Parametreyi `Parameters` koleksiyona ekleyin.<br />- `ParameterDirection.Output` Parametreyi çıkış olarak tanımlamak için kullanın.|
|NC-10|Bağlantıyı açmak için try-catch-finally bloğu ekleyin, saklı yordamı çalıştırın, özel durumları işleyin ve bağlantıyı kapatın.|
|NC-11|`conn`NC-6 ' da oluşturduğunuz bağlantıyı () açın.|
|NC-12|`ExecuteNonQuery` `cmdNewCustomer` Saklı yordamını çalıştırmak için yöntemini kullanın `Sales.uspNewCustomer` . Bu saklı yordam `INSERT` bir sorgu değil, bir ifade çalıştırır.|
|NC-13|`@CustomerID`Değer, veritabanından BIR kimlik değeri olarak döndürülür. Bir tamsayı olduğundan, bunu **MÜŞTERI kimliği** metin kutusunda göstermek için bir dizeye dönüştürmeniz gerekir.<br /><br /> - `parsedCustomerID` NC-2 ' de bildirdiniz.<br />- `@CustomerID` Değerini `parsedCustomerID` daha sonra kullanmak üzere depolayın.<br />-Döndürülen müşteri KIMLIĞINI bir dizeye dönüştürün ve içine ekleyin `txtCustomerID.Text` .|
|NC-14|Bu örnek için basit (üretim kalitesi olmayan) bir catch yan tümcesi ekleyin.|
|NC-15|Bağlantıyı tamamladıktan sonra bağlantı havuzuna yayımlanabilmesi için her zaman bir bağlantıyı kapatın. Bkz. [SQL Server bağlantı havuzu (ADO.net)](https://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx).|
|NC-16|Bir müşteri adının mevcut olduğunu doğrulamak için bir yöntem tanımlayın.<br /><br /> -Metin kutusu boşsa, `false` hesap oluşturmak için bir ad gerektiğinden bir ileti ve dönüş görüntüleyin.<br />-Metin kutusu boş değilse, döndürün `true` .|
|NC-17|Düğme için Click olay işleyicisine kod ekleyin `btnPlaceOrder` .|
|NC-18|Gerekli giriş yoksa çalıştırılmaması için, çağrı `isPlaceOrderReady` olay kodu etrafında sarmalayın `btnPlaceOrder_Click` `uspPlaceNewOrder` .|
|NC-19 ile NC-25|Bu kod bölümleri, olay işleyicisi için eklediğiniz koda benzer `btnCreateAccount_Click` .<br /><br /> -NC-19. Nesnesini oluşturun `SqlCommand` `cmdNewOrder` ve `Sales.uspPlaceOrder` saklı yordam olarak belirtin.<br />-NC-20 ila NC-23, saklı yordamın giriş parametreleridir.<br />-NC-24. `@RC` , veritabanından üretilen sıra KIMLIĞI olan bir dönüş değeri içerir. Bu Parametrenin yönü olarak belirtilir `ReturnValue` .<br />-NC-25. Sıra KIMLIĞI değerini `orderID` NC-2 ' de bildirdiğiniz değişkende depolayın ve değeri bir ileti kutusunda görüntüleyin.|
|NC-26|Bir müşteri KIMLIĞININ mevcut olduğunu ve ' de bir tutarın bulunduğunu doğrulamak için bir yöntem tanımlayın `numOrderAmount` .|
|NC-27|`ClearForm` `btnAddAnotherAccount` Click olay işleyicisindeki yöntemi çağırın.|
|NC-28|`ClearForm`Başka bir müşteri eklemek istiyorsanız formdaki değerleri temizlemek için yöntemi oluşturun.|
|NC29|NewCustomer formunu kapatın ve odağı gezinti formuna döndürün.|

### <a name="fillorcancel-form"></a>FillOrCancel formu
 FillorCancel formu, bir sipariş KIMLIĞI girerken siparişi döndürmek için bir sorgu çalıştırır ve **siparişi bul** düğmesini seçersiniz. Döndürülen satır salt okunurdur bir veri kılavuzunda görünür. Siparişi **Iptal et** düğmesini seçerseniz siparişi iptal edildi (X) olarak işaretleyebilirsiniz veya sırayı **doldur** düğmesini seçerseniz sırayı doldurulmuş (F) olarak işaretleyebilirsiniz. **Siparişi bul** düğmesini tekrar seçerseniz, güncelleştirilmiş satır görüntülenir.

#### <a name="create-event-handlers"></a>Olay işleyicileri oluşturma
 Form üzerindeki dört düğme için boş tıklama olay işleyicileri oluşturun.

#### <a name="create-code-for-fillorcancel"></a>FillOrCancel için kod oluştur
 FillOrCancel formuna aşağıdaki kodu ekleyin. Numaralandırılmış açıklamaları ve kodu izleyen tabloyu kullanarak kod blokları aracılığıyla ilerleyin.

```csharp
using System;
using System.Collections.Generic;
using System.ComponentModel;
using System.Data;
using System.Drawing;
using System.Linq;
using System.Text;
using System.Threading.Tasks;
using System.Windows.Forms;
//FC-1 More namespaces.
using System.Text.RegularExpressions;
using System.Data.SqlClient;
using System.Configuration;

namespace SimpleDataApp
{
    public partial class FillOrCancel : Form
    {
        //FC-2 Storage for OrderID.
        private int parsedOrderID;

        //FC-3 Specify a connection string.
        string connstr = SimpleDataApp.Utility.GetConnectionString();

        public FillOrCancel()
        {
            InitializeComponent();
        }

        //FC-4 Find an order.
        private void btnFindByOrderID_Click(object sender, EventArgs e)
        {
            //FC-5 Prepare the connection and the command.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //Define a query string that has a parameter for orderID.
                string sql = "select * from Sales.Orders where orderID = @orderID";

                //Create a SqlCommand object.
                SqlCommand cmdOrderID = new SqlCommand(sql, conn);

                //Define the @orderID parameter and its value.
                cmdOrderID.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdOrderID.Parameters["@orderID"].Value = parsedOrderID;

                //try-catch-finally
                try
                {
                    //FC-6 Run the command and display the results.
                    //Open the connection.
                    conn.Open();

                    //Run the command by using SqlDataReader.
                    SqlDataReader rdr = cmdOrderID.ExecuteReader();

                    //Create a data table to hold the retrieved data.
                    DataTable dataTable = new DataTable();

                    //Load the data from SqlDataReader into the data table.
                    dataTable.Load(rdr);

                    //Display the data from the data table in the data grid view.
                    this.dgvCustomerOrders.DataSource = dataTable;

                    //Close the SqlDataReader.
                    rdr.Close();
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("The requested order could not be loaded into the form.");
                }
                finally
                {
                    //Close the connection.
                    conn.Close();
                }
            }
        }

        //FC-7 Cancel an order.
        private void btnCancelOrder_Click(object sender, EventArgs e)
        {
            //Set up and run stored procedure only if OrderID is ready.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                // Create command and identify it as a stored procedure.
                SqlCommand cmdCancelOrder = new SqlCommand("Sales.uspCancelOrder", conn);
                cmdCancelOrder.CommandType = CommandType.StoredProcedure;

                cmdCancelOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdCancelOrder.Parameters["@orderID"].Value = parsedOrderID;

                // try-catch-finally
                try
                {
                    // Open the connection.
                    conn.Open();

                    // Run the cmdCancelOrder command.
                    cmdCancelOrder.ExecuteNonQuery();
                }
                // A simple catch.
                catch
                {
                    MessageBox.Show("The cancel operation was not completed.");
                }
                finally
                {
                    //Close connection.
                    conn.Close();
                }
            }
        }

        //FC-8 Fill an order.
        private void btnFillOrder_Click(object sender, EventArgs e)
        {
            //Set up and run stored procedure only if OrderID is ready.
            if (isOrderID())
            {
                //Create the connection.
                SqlConnection conn = new SqlConnection(connstr);

                //Create command and identify it as a stored procedure.
                SqlCommand cmdFillOrder = new SqlCommand("Sales.uspFillOrder", conn);
                cmdFillOrder.CommandType = CommandType.StoredProcedure;

                // Add input parameter from the stored procedure.
                cmdFillOrder.Parameters.Add(new SqlParameter("@orderID", SqlDbType.Int));
                cmdFillOrder.Parameters["@orderID"].Value = parsedOrderID;

                //Add the second input parameter.
                cmdFillOrder.Parameters.Add(new SqlParameter("@FilledDate", SqlDbType.DateTime, 8));
                cmdFillOrder.Parameters["@FilledDate"].Value = dtpFillDate.Value;

                //try-catch-finally
                try
                {
                    //Open the connection.
                    conn.Open();

                    //Run the cmdFillOrder command.
                    cmdFillOrder.ExecuteNonQuery();
                }
                catch
                {
                    //A simple catch.
                    MessageBox.Show("The fill operation was not completed.");
                }
                finally
                {
                    //Close the connection.
                    conn.Close();
                }
            }
        }

        //FC-9 Verify that OrderID is ready.
        private bool isOrderID()
        {

            //Check for input in the Order ID text box.
            if (txtOrderID.Text == "")
            {
                MessageBox.Show("Please specify the Order ID.");
                return false;
            }

            // Check for characters other than integers.
            else if (Regex.IsMatch(txtOrderID.Text, @"^\D*$"))
            {
               //Show message and clear input.
                MessageBox.Show("Please specify integers only.");
                txtOrderID.Clear();
                return false;
            }
            else
            {
                //Convert the text in the text box to an integer to send to the database.
                parsedOrderID = Int32.Parse(txtOrderID.Text);
                return true;
            }
        }

        //Close the form.
        private void btnFinishUpdates_Click(object sender, EventArgs e)
        {
            this.Close();
        }
    }
}
```

```vb
Imports System
Imports System.Collections.Generic
Imports System.ComponentModel
Imports System.Data
Imports System.Drawing
Imports System.Linq
Imports System.Text
Imports System.Threading.Tasks
Imports System.Windows.Forms
' FC-1 More namespaces.
Imports System.Text.RegularExpressions
Imports System.Data.SqlClient
Imports System.Configuration

Namespace SimpleDataApp
    Partial Public Class FillOrCancel
        Inherits Form
        ' FC-2 Storage for OrderID.
        Private parsedOrderID As Integer

        ' FC-3 Specify a connection string.
        Private connstr As String = SimpleDataApp.Utility.GetConnectionString()

        Public Sub New()
            InitializeComponent()
        End Sub

        ' FC-4 Find an order.
        Private Sub btnFindByOrderID_Click() Handles btnFindByOrderID.Click

            ' FC-5 Prepare the connection and the command.

            If isOrderID() Then
                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Define the query string that has a parameter for orderID.
                Dim sql As String = "select * from Sales.Orders where orderID = @orderID"

                ' Create a SqlCommand object.
                Dim cmdOrderID As New SqlCommand(sql, conn)

                ' Define the @orderID parameter and its value.
                cmdOrderID.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdOrderID.Parameters("@orderID").Value = parsedOrderID

                ' try-catch-finally
                Try
                    ' FC-6 Run the command and display the results.
                    ' Open connection.
                    conn.Open()

                    ' Run the command by using SqlDataReader.
                    Dim rdr As SqlDataReader = cmdOrderID.ExecuteReader()

                    ' Create a data table to hold the retrieved data.
                    Dim dataTable As New DataTable()

                    ' Load the data from SqlDataReader into the data table.
                    dataTable.Load(rdr)

                    ' Display the data from the data table in the data grid view.
                    Me.dgvCustomerOrders.DataSource = dataTable

                    ' Close the SqlDataReader.
                    rdr.Close()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The requested order could not be loaded into the form.")
                Finally
                    ' Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-7 Cancel an order.
        Private Sub btnCancelOrder_Click() Handles btnCancelOrder.Click

            ' Set up and run stored procedure only if OrderID is ready.
            If isOrderID() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Create the command and identify it as a stored procedure.
                Dim cmdCancelOrder As New SqlCommand("Sales.uspCancelOrder", conn)
                cmdCancelOrder.CommandType = CommandType.StoredProcedure

                ' Add input parameter from the stored procedure.
                cmdCancelOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdCancelOrder.Parameters("@orderID").Value = parsedOrderID

                ' try-catch-finally
                Try
                    ' Open the connection.
                    conn.Open()

                    ' Run the cmdCancelOrder command.
                    cmdCancelOrder.ExecuteNonQuery()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The cancel operation was not completed.")
                Finally
                    ' Close connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-8 Fill an order.
        Private Sub btnFillOrder_Click() Handles btnFillOrder.Click

            ' Set up and run stored procedure only if OrderID is ready.
            If isOrderID() Then

                ' Create the connection.
                Dim conn As New SqlConnection(connstr)

                ' Create command and identify it as a stored procedure.
                Dim cmdFillOrder As New SqlCommand("Sales.uspFillOrder", conn)
                cmdFillOrder.CommandType = CommandType.StoredProcedure

                ' Add input parameter from the stored procedure.
                cmdFillOrder.Parameters.Add(New SqlParameter("@orderID", SqlDbType.Int))
                cmdFillOrder.Parameters("@orderID").Value = parsedOrderID

                ' Add second input parameter.
                cmdFillOrder.Parameters.Add(New SqlParameter("@FilledDate", SqlDbType.DateTime, 8))
                cmdFillOrder.Parameters("@FilledDate").Value = dtpFillDate.Value

                ' try-catch-finally
                Try
                    ' Open the connection.
                    conn.Open()

                    ' Run the cmdFillOrder command.
                    cmdFillOrder.ExecuteNonQuery()
                Catch
                    ' A simple catch.
                    MessageBox.Show("The fill operation was not completed.")
                Finally
                    ' Close the connection.
                    conn.Close()
                End Try
            End If
        End Sub

        ' FC-9 Verify that OrderID is ready.
        Private Function isOrderID() As Boolean

            ' Check for input in the Order ID text box.
            If txtOrderID.Text = "" Then
                MessageBox.Show("Please specify the Order ID.")
                Return False

                ' Check for characters other than integers.
            ElseIf Regex.IsMatch(txtOrderID.Text, "^\D*$") Then

                ' Show message and clear input.
                MessageBox.Show("Please specify integers only.")
                txtOrderID.Clear()
                Return False

            Else
                ' Convert the text in the text box to an integer to send to the database.
                parsedOrderID = Int32.Parse(txtOrderID.Text)
                Return True

            End If
        End Function

        ' Close the form.
        Private Sub btnFinishUpdates_Click() Handles btnFinishUpdates.Click
            Me.Close()
        End Sub
    End Class
End Namespace
```

|Yorum|Description|
|-------------|-----------------|
|FC-1|`System.Data.SqlClient` `System.Configuration` `System.Text.RegularExpressions` Ad alanları listesine, ve ekleyin.|
|FC-2|Değişkeni bildirin `parsedOrderID` .|
|FC-3|`GetConnectionString`Uygulama yapılandırma dosyasından bağlantı dizesini almak için yöntemini çağırın ve değeri `connstr` dize değişkeninde depolayın.|
|FC-4|İçin Click olay işleyicisine kod ekleyin `btnFindOrderByID` .|
|FC-5|Bu görevler, bir SQL ifadesini veya saklı yordamı çalıştırmayı denemeden önce gereklidir.<br /><br /> -Bir `SqlConnection` nesne oluşturun.<br />-SQL ifadesini tanımlayın veya saklı yordamın adını belirtin. (Bu durumda, bir ifadesini çalıştıracaksınız `SELECT` .)<br />-Bir `SqlCommand` nesne oluşturun.<br />-SQL deyimin veya saklı yordamın parametrelerini tanımlayın.|
|FC-6|Bu kod `SqlDataReader` `DataTable` , sorgu sonucunu almak ve göstermek için ve kullanır.<br /><br /> -Bağlantıyı açın.<br />- `SqlDataReader` Yöntemini çalıştırarak bir nesnesi oluşturun `rdr` `ExecuteReader` `cmdOrderID` .<br />- `DataTable` Alınan verileri tutacak bir nesne oluşturun.<br />-Nesne içindeki verileri nesnesine yükleyin `SqlDataReader` `DataTable` .<br />-Veri `DataTable` Kılavuzu görünümü için olarak belirterek verileri veri kılavuzu görünümünde görüntüleyin `DataSource` .<br />-Kapat `SqlDataReader` .|
|FC-7|İçin Click olay işleyicisine kod ekleyin `btnCancelOrder` . Bu kod, `Sales.uspCancelOrder` saklı yordamı çalıştırır.|
|FC-8|İçin Click olay işleyicisine kod ekleyin `btnFillOrder` . Bu kod, `Sales.uspFillOrder` saklı yordamı çalıştırır.|
|FC-9|`OrderID`Nesnesine bir parametre olarak gönderilmeye hazırlanma olduğunu doğrulamak için bir yöntem oluşturun `SqlCommand` .<br /><br /> -' De bir KIMLIK girildiğinden emin olun `txtOrderID` .<br />- `Regex.IsMatch` Tamsayı olmayan karakterler için basit bir denetim tanımlamak üzere kullanın.<br />- `parsedOrderID` DEĞIŞKENI FC-2 konumunda bildirdiniz.<br />-Giriş geçerliyse, metni bir tamsayıya dönüştürün ve değeri `parsedOrderID` değişkende depolayın.<br />-Yöntemini,,, `isOrderID` `btnFindByOrderID` `btnCancelOrder` ve `btnFillOrder` olay işleyiciler ' a sarmalayın.|

## <a name="test-your-application"></a><a name="BKMK_testyourapplication"></a> Uygulamanızı test etme
 Her bir tıklama olayı işleyicisini kodladıktan sonra ve sonra kodlamayı tamamladıktan sonra uygulamanızı derlemek ve test etmek için F5 tuşunu seçin.
