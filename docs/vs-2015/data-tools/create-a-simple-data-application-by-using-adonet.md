---
title: ADO.NET을 사용 하 여 간단한 데이터 응용 프로그램 만들기 | Microsoft Docs
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 70fca5b1329dc9091e0672b41de0798d93aba01a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65705176"
---
# <a name="create-a-simple-data-application-by-using-adonet"></a>ADO.NET을 사용하여 간단한 데이터 애플리케이션 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터베이스의 데이터를 조작하는 애플리케이션을 만들면 연결 문자열 정의, 데이터 삽입 및 저장 프로시저 실행과 같은 기본 작업을 수행합니다. 이 항목에 따라 Visual C# 또는 Visual Basic 및 ADO.NET을 사용 하 여 간단한 Windows Forms "데이터 폼" 응용 프로그램 내에서 데이터베이스와 상호 작용 하는 방법을 확인할 수 있습니다.  모든.NET 데이터 기술-LINQ to SQL과 Entity Framework 데이터 집합을 포함 하 여, 궁극적으로이 문서에 나와 있는 것과 매우 유사한 단계를 수행 합니다.  
  
 이 문서는 데이터베이스에서 데이터를 매우 빠르게 방식으로 참여 하는 간단한 방법을 보여 줍니다. 응용 프로그램을 trivial이 아닌 방법으로 데이터를 수정 하 고 데이터베이스를 업데이트 하는 경우에 Entity Framework를 사용 하 여 및 데이터 바인딩 기본 데이터의 변경 내용에 사용자 인터페이스 컨트롤을 자동으로 동기화를 사용 해야 합니다.  
  
> [!IMPORTANT]
> 코드를 간단히 유지하기 위해 프로덕션에 사용하는 예외 처리는 포함되어 있지 않습니다.  
  
 **항목 내용**  
  
- [샘플 데이터베이스 설정](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_setupthesampledatabase)  
  
- [폼 만들기 및 컨트롤 추가](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_createtheformsandaddcontrols)  
  
- [연결 문자열 저장](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_storetheconnectionstring)  
  
- [연결 문자열 검색](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_retrievetheconnectionstring)  
  
- [폼에 대 한 코드 작성](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_writethecodefortheforms)  
  
- [응용 프로그램 테스트](../data-tools/create-a-simple-data-application-by-using-adonet.md#BKMK_testyourapplication)  
  
## <a name="prerequisites"></a>전제 조건  
 애플리케이션을 만들려면 다음이 필요 합니다.  
  
- Visual Studio Community Edition.  
  
- SQL Server Express LocalDB.  
  
- 단계를 수행 하 여 만든 작은 예제 데이터베이스 [스크립트를 사용 하 여 SQL 데이터베이스를 만들](../data-tools/create-a-sql-database-by-using-a-script.md)합니다.  
  
- 데이터베이스에 대해 설정한 연결 문자열입니다. 열어이 값을 찾을 수 있습니다 **SQL Server 개체 탐색기**데이터베이스에 대 한 바로 가기 메뉴를 열고, 선택 **속성**, 고 다음으로 스크롤 하는 **ConnectionString** 속성입니다.  
  
  이 항목에서는 사용자가 Visual Studio IDE의 기본 기능에 익숙하고 Windows Forms 애플리케이션 작성, 프로젝트에 폼 추가, 폼에 단추 및 기타 컨트롤 배치, 이러한 컨트롤의 속성 설정 및 간단한 이벤트 코드 작성을 수행할 수 있다고 가정합니다. 이러한 작업에 익숙하지 경우 완료 하는 것이 좋습니다 합니다 [Getting Started with Visual C# 및 Visual Basic](../ide/getting-started-with-visual-csharp-and-visual-basic.md) 이 항목에서는 시작 하기 전에 합니다.  
  
## <a name="BKMK_setupthesampledatabase"></a> 샘플 데이터베이스 설정  
 이 연습의 샘플 데이터베이스는 고객 및 주문 테이블로 구성되어 있습니다. 테이블에는 처음에 데이터가 없지만 사용자가 만드는 애플리케이션을 실행할 때 데이터가 추가됩니다. 데이터베이스에는 5개의 간단한 저장 프로시저도 있습니다. [스크립트를 사용 하 여 SQL database 만들기](../data-tools/create-a-sql-database-by-using-a-script.md) 테이블, 기본 및 외래 키, 제약 조건 및 저장된 프로시저를 만드는 TRANSACT-SQL 스크립트가 들어 있습니다.  
  
## <a name="BKMK_createtheformsandaddcontrols"></a> 폼 만들기 및 컨트롤 추가  
  
1. Windows Forms 응용 프로그램의 경우 프로젝트를 만들고 SimpleDataApp 이름입니다.  
  
    Visual Studio에서 프로젝트와 Form1이라는 빈 Windows 폼을 포함한 여러 파일을 만듭니다.  
  
2. 프로젝트에 두 개의 Windows 양식을 추가하여 총 세 개의 양식을 만든 다음, 다음 이름을 지정합니다.  
  
   - 탐색  
  
   - NewCustomer  
  
   - FillOrCancel  
  
3. 각 폼에 대해 다음 그림에 나오는 텍스트 상자, 단추 및 기타 컨트롤을 추가합니다. 각 컨트롤에 대해 테이블이 설명하는 속성을 설정합니다.  
  
   > [!NOTE]
   > 그룹 상자 및 레이블 컨트롤도 선명성을 더해 주지만 코드에서는 사용하지 않습니다.  
  
   **탐색 양식**  
  
   ![탐색 대화 상자](../data-tools/media/simpleappnav.png "SimpleAppNav")  
  
|Navigation 폼 컨트롤|속성|  
|--------------------------------------|----------------|  
|단추|Name = btnGoToAdd|  
|단추|Name = btnGoToFillOrCancel|  
|단추|Name = btnExit|  
  
 **NewCustomer 양식**  
  
 ![새 고객을 추가 하 고 주문 하기](../data-tools/media/simpleappnewcust.png "SimpleAppNewCust")  
  
|NewCustomer 폼 컨트롤|속성|  
|---------------------------------------|----------------|  
|TextBox|Name = txtCustomerName|  
|TextBox|Name = txtCustomerID<br /><br /> Readonly = True|  
|단추|Name = btnCreateAccount|  
|NumericUpdown|DecimalPlaces = 0<br /><br /> Maximum = 5000<br /><br /> Name = numOrderAmount|  
|DateTimePicker|Format = Short<br /><br /> Name = dtpOrderDate|  
|단추|Name = btnPlaceOrder|  
|단추|Name = btnAddAnotherAccount|  
|단추|Name = btnAddFinish|  
  
 **FillOrCancel 양식**  
  
 ![주문 입력 또는 취소](../data-tools/media/simpleappcancelfill.png "SimpleAppCancelFill")  
  
|FillOrCancel 폼 컨트롤|속성|  
|----------------------------------------|----------------|  
|TextBox|Name = txtOrderID|  
|단추|Name = btnFindByOrderID|  
|DateTimePicker|Format = Short<br /><br /> Name = dtpFillDate|  
|DataGridView|Name = dgvCustomerOrders<br /><br /> Readonly = True<br /><br /> RowHeadersVisible = False|  
|단추|Name = btnCancelOrder|  
|단추|Name = btnFillOrder|  
|단추|Name = btnFinishUpdates|  
  
## <a name="BKMK_storetheconnectionstring"></a> 연결 문자열 저장  
 애플리케이션이 데이터베이스에 대한 연결을 열려면 애플리케이션에는 연결 문자열에 액세스할 수 있어야 합니다. 각 폼에 문자열을 수동으로 입력를 방지 하려면 프로젝트에서 app.config 파일에 문자열을 저장 하 고 응용 프로그램의 폼에서 메서드를 호출할 때 문자열을 반환 하는 메서드를 만듭니다.  
  
 연결 문자열을 찾을 수 있습니다 **SQL Server 개체 탐색기** 데이터베이스를 마우스 오른쪽 단추로 클릭를 선택 하 여 **속성**를 찾아 ConnectionString 속성입니다. Ctrl + A를 사용 하 여 문자열을 선택 합니다.  
  
1. **솔루션 탐색기**를 선택 합니다 **속성** 노드는 프로젝트를 선택한 후 아래의 **생성 되는 Settings.settings**합니다.  
  
2. 에 **이름을** 열, 입력 `connString`합니다.  
  
3. 에 **형식** 목록에서 **(문자열)** 합니다.  
  
4. 에 **범위** 목록에서 **응용 프로그램**합니다.  
  
5. 에 **값** 열 (하지 않고 따옴표 외부), 연결 문자열을 입력 하 고 다음 변경 내용을 저장 합니다.  
  
> [!NOTE]
> 실제 응용 프로그램에서 연결 문자열을 안전 하 게에 설명 된 대로 저장 해야 [연결 문자열 및 구성 파일](https://msdn.microsoft.com/library/37df2641-661e-407a-a3fb-7bf9540f01e8)합니다.  
  
## <a name="BKMK_retrievetheconnectionstring"></a> 연결 문자열 검색  
  
1. 메뉴 모음에서 선택 **프로젝트** > **참조 추가**, 한 다음 System.Configuration.dll에 대 한 참조를 추가 합니다.  
  
2. 메뉴 모음에서 선택 **프로젝트** > **클래스 추가** 클래스 파일을 프로젝트에 추가 하 여 다음 파일 이름을 `Utility`입니다.  
  
     Visual Studio에서 파일을 만들고 및에 표시 **솔루션 탐색기**합니다.  
  
3. 유틸리티 파일에서 자리 표시자 코드를 다음 코드로 바꿉니다. 코드 섹션을 식별하는 번호가 매겨진 주석(Util- 접두사 포함)을 주목하세요. 코드 아래 표에 요점이 요약되어 있습니다.  
  
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
  
    |주석|설명|  
    |-------------|-----------------|  
    |Util-1|`System.Configuration` 네임스페이스를 추가합니다.|  
    |Util-2|`returnValue` 변수를 정의하고 `null`(C#) 또는 `Nothing`(Visual Basic)으로 초기화합니다.|  
    |Util-3|입력 한 경우에 `connString` 연결 문자열의 이름으로는 **속성** 지정 해야 창 `"SimpleDataApp.Properties.Settings.connString"` (C#) 또는 `"SimpleDataApp.My.MySettings.connString"` (Visual Basic) 코드에서입니다.|  
  
## <a name="BKMK_writethecodefortheforms"></a> 폼에 대 한 코드 작성  
 이 섹션에서는 각 폼에서 수행되는 작업에 대한 간단한 개요를 포함하며, 폼을 만드는 코드를 보여 줍니다. 번호가 매겨진 주석은 해당 코드 섹션을 식별합니다.  
  
### <a name="navigation-form"></a>Navigation 폼  
 애플리케이션을 실행하면 Navigation 폼이 열립니다. **계정 추가** 단추는 NewCustomer 양식을 엽니다. **주문 이행 또는 취소** 단추를 누르면 FillOrCancel 양식이 열립니다. **끝내기** 단추를 클릭하면 애플리케이션이 닫힙니다.  
  
#### <a name="make-the-navigation-form-the-startup-form"></a>Navigation 폼을 시작 폼으로 만들기  
 사용 하는 C#의 경우 **솔루션 탐색기**Program.cs를 열고 변경 하는 `Application.Run` 이 줄: `Application.Run(new Navigation());`  
  
 Visual Basic을 사용 하는 경우 **솔루션 탐색기**오픈 합니다 **속성** 창에서를 **응용 프로그램** 탭을 선택한 후  **SimpleDataApp.Navigation** 에 **시작 폼** 목록입니다.  
  
#### <a name="create-event-handlers"></a>이벤트 처리기 만들기  
 빈 이벤트 처리기 메서드를 만드는 폼에 단추 세 개를 두 번 클릭 합니다.  
  
#### <a name="create-code-for-navigation"></a>탐색 코드 만들기  
 Navigation 폼에서 기존 코드를 다음 코드로 바꿉니다.  
  
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
  
### <a name="newcustomer-form"></a>NewCustomer 폼  
 고객 이름을 입력 하 고 다음을 선택 합니다 **계정 만들기** 단추 NewCustomer 폼은 고객 계정을 만들고 SQL Server에서 ID 값을 새 계정 번호로 반환 합니다. 금액과 주문 날짜를 지정 하 고 선택 하 여 새 계정에 대 한 주문을 입력 한 다음 합니다 **주문** 단추입니다.  
  
#### <a name="create-event-handlers"></a>이벤트 처리기 만들기  
 폼의 각 단추에 대해 빈 Click 이벤트 처리기를 만듭니다.  
  
#### <a name="create-code-for-newcustomer"></a>NewCustomer 코드 만들기  
 NewCustomer 폼에 다음 코드를 추가합니다. 코드 뒤의 번호가 매겨진 주석과 테이블을 사용하여 각 코드 블록을 단계별로 실행합니다.  
  
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
  
|주석|설명|  
|-------------|-----------------|  
|NC-1|추가 `System.Data.SqlClient` 고 `System.Configuration` 네임 스페이스의 목록입니다.|  
|NC-2|나중에 사용할 `parsedCustomerID` 및 `orderID` 변수를 선언합니다.|  
|NC-3|`GetConnectionString` 메서드를 호출하여 응용 프로그램 구성 파일에서 연결 문자열을 가져오고 `connstr` 문자열 변수에 값을 저장합니다.|  
|NC-4|`btnCreateAccount` 단추에 대한 클릭 이벤트 처리기에 코드를 추가합니다.|  
|NC-5|고객 이름이 있는 경우에만 `uspNewCustomer`가 실행되도록 Click 이벤트 코드 주변의 `isCustomerName`에 대한 호출을 래핑합니다.|  
|NC-6|`SqlConnection` 개체(`conn`)를 만들어 `connstr`의 연결 문자열에 전달합니다.|  
|NC-7|`SqlCommand` 개체(`cmdNewCustomer`)를 만듭니다.<br /><br /> -지정 `Sales.uspNewCustomer` 로 저장된 프로시저를 실행 합니다.<br />-사용 된 `CommandType` 명령이 저장된 프로시저 임을 지정 하려면 속성입니다.|  
|NC-8|저장 프로시저에서 `@CustomerName` 입력 매개 변수를 추가합니다.<br /><br /> -매개 변수를 추가 합니다 `Parameters` 컬렉션입니다.<br />-사용 된 `SqlDbType` 매개 변수 형식을 nvarchar(40)로 지정 하는 열거형입니다.<br />-지정 `txtCustomerName.Text` 원본으로 합니다.|  
|NC-9|저장 프로시저에서 출력 매개 변수를 추가합니다.<br /><br /> -매개 변수를 추가 합니다 `Parameters` 컬렉션입니다.<br />-사용 `ParameterDirection.Output` 출력으로 매개 변수를 식별 합니다.|  
|NC-10|Try – Catch – Finally 블록을 연결 열기, 저장된 프로시저를 실행, 예외를 처리 및 다음 연결을 닫는 추가 합니다.|  
|NC-11|NC-6에서 만든 연결(`conn`)을 엽니다.|  
|NC-12|사용 합니다 `ExecuteNonQuery` 에 대 한 메서드 `cmdNewCustomer` 실행 하는 `Sales.uspNewCustomer` 저장 프로시저. 이 저장 프로시저가 실행 될은 `INSERT` 문, 쿼리 없습니다.|  
|NC-13|데이터베이스에서 IDENTITY 값으로 `@CustomerID` 값이 반환됩니다. 에 표시할 문자열로 변환 해야 하는 정수 이기 때문에 합니다 **고객 ID** 입력란입니다.<br /><br /> -선언 하면 `parsedCustomerID` NC-2에서 합니다.<br />-저장 된 `@CustomerID` 값 `parsedCustomerID` 나중에 사용할 수 있습니다.<br />-반환 된 고객 ID를 문자열로 변환 하 고에 삽입 `txtCustomerID.Text`합니다.|  
|NC-14|이 샘플에서는 간단한 (비프로덕션 품질) catch 절을 추가 합니다.|  
|NC-15|연결을 사용한 후에는 반드시 닫아야 연결 풀로 해제됩니다. 참조 [SQL Server 연결 풀링 (ADO.NET)](https://msdn.microsoft.com/library/8xx3tyca\(l=en-us,v=VS.110\).aspx)합니다.|  
|NC-16|고객 이름이 있는지 확인하는 메서드를 정의합니다.<br /><br /> -텍스트 상자가 비어 있는 경우 메시지를 표시 하 고 반환 `false`이므로 계정을 만들려면 이름이 필요 합니다.<br />-텍스트 상자가 비어 있지 않은 경우 반환 `true`합니다.|  
|NC-17|`btnPlaceOrder` 단추에 대한 클릭 이벤트 처리기에 코드를 추가합니다.|  
|NC-18|필수 입력이 없는 경우 `uspPlaceNewOrder`가 실행되지 않도록 `btnPlaceOrder_Click` 이벤트 코드 주변의 `isPlaceOrderReady`에 대한 호출을 래핑합니다.|  
|NC-19~NC-25|이러한 코드 섹션은 `btnCreateAccount_Click` 이벤트 처리기에 추가한 코드와 유사합니다.<br /><br /> -   NC-19. `SqlCommand` 개체인 `cmdNewOrder`를 만들고 `Sales.uspPlaceOrder`를 저장 프로시저로 지정합니다.<br />-NC-20-23 NC는 저장된 프로시저에 대 한 입력된 매개 변수입니다.<br />-   NC-24. `@RC`에는 데이터베이스에서 생성된 주문 ID인 반환 값이 포함됩니다. 이 매개 변수의 방향은 `ReturnValue`로 지정됩니다.<br />-   NC-25. NC-2에서 선언한 `orderID` 변수에 주문 ID 값을 저장하고 값을 메시지 상자에 표시합니다.|  
|NC-26|고객 ID가 있는지와 금액이 `numOrderAmount`에 지정되었는지 확인할 수 있는 메서드를 정의합니다.|  
|NC-27|`btnAddAnotherAccount` 클릭 이벤트 처리기에서 `ClearForm` 메서드를 호출합니다.|  
|NC-28|다른 고객을 추가하려면 폼에서 값을 지우는 `ClearForm` 메서드를 만듭니다.|  
|NC29|NewCustomer 폼을 닫고 탐색 폼으로 포커스를 되돌립니다.|  
  
### <a name="fillorcancel-form"></a>FillOrCancel 폼  
 FillorCancel 폼 주문 ID를 입력 하 고 선택 하면 주문을 반환 하는 쿼리를 실행 합니다 **주문 찾기** 단추입니다. 반환되는 행은 읽기 전용 데이터 표에 표시됩니다. 선택할 경우 주문을 취소 (X)으로 표시할 수 있습니다는 **주문 취소** 하거나 단추를 표시할 수 있습니다 순서 채워진된 (F)을 선택 합니다 **주문** 단추입니다. 선택 하는 경우는 **주문 찾기** 단추를 다시 업데이트 된 행은 표시 됩니다.  
  
#### <a name="create-event-handlers"></a>이벤트 처리기 만들기  
 폼의 네 단추에 대해 빈 Click 이벤트 처리기를 만듭니다.  
  
#### <a name="create-code-for-fillorcancel"></a>FillOrCancel 코드 만들기  
 FillOrCancel 폼에 다음 코드를 추가합니다. 코드 뒤의 번호가 매겨진 주석과 테이블을 사용하여 코드 블록을 단계별로 실행합니다.  
  
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
  
|주석|설명|  
|-------------|-----------------|  
|FC-1|추가 `System.Data.SqlClient`, `System.Configuration`, 및 `System.Text.RegularExpressions` 네임 스페이스의 목록입니다.|  
|FC-2|`parsedOrderID` 변수를 선언합니다.|  
|FC-3|`GetConnectionString` 메서드를 호출하여 응용 프로그램 구성 파일에서 연결 문자열을 가져오고 `connstr` 문자열 변수에 값을 저장합니다.|  
|FC-4|`btnFindOrderByID`에 대한 Click 이벤트 처리기에 추가합니다.|  
|FC-5|SQL 문 또는 저장 프로시저를 실행하기 전에 다음 작업을 수행해야 합니다.<br /><br /> -만들기는 `SqlConnection` 개체입니다.<br />-SQL 문을 정의 하거나 저장된 프로시저의 이름을 지정 합니다. 이 경우 `SELECT` 문을 실행합니다.<br />-만들기는 `SqlCommand` 개체입니다.<br />-SQL 문이나 저장된 프로시저에 대 한 모든 매개 변수를 정의 합니다.|  
|FC-6|이 코드는 `SqlDataReader` 및 `DataTable`을 사용하여 쿼리 결과를 검색 및 표시합니다.<br /><br /> -연결을 엽니다.<br />-만들기를 `SqlDataReader` 개체를 `rdr`를 실행 하 여는 `ExecuteReader` 메서드를 `cmdOrderID`입니다.<br />-만들기는 `DataTable` 검색된 데이터를 보관 하는 개체입니다.<br />-데이터를 로드 합니다 `SqlDataReader` 개체를 `DataTable` 개체입니다.<br />-데이터 데이터 그리드 보기에서 지정 하 여 표시할 `DataTable` 으로 `DataSource` 데이터 그리드 보기에 대 한 합니다.<br />-닫기 `SqlDataReader`합니다.|  
|FC-7|`btnCancelOrder`에 대한 Click 이벤트 처리기에 추가합니다. 이 코드는 `Sales.uspCancelOrder` 저장 프로시저를 실행합니다.|  
|FC-8|`btnFillOrder`에 대한 Click 이벤트 처리기에 추가합니다. 이 코드는 `Sales.uspFillOrder` 저장 프로시저를 실행합니다.|  
|FC-9|확인 하는 메서드를 만듭니다 `OrderID` 매개 변수로 전송 될 준비가 되는 `SqlCommand` 개체입니다.<br /><br /> -확인에 ID를 입력 된 않도록 `txtOrderID`합니다.<br />-사용 `Regex.IsMatch` 에 정수가 아닌 문자에 대 한 간단한 검사를 정의 합니다.<br />-선언 하는 `parsedOrderID` FC 2에 있는 변수입니다.<br />-올바르면 입력 텍스트를 정수로 변환 하 고 값을 저장 합니다 `parsedOrderID` 변수입니다.<br />-줄 바꿈 합니다 `isOrderID` 관련 메서드는 `btnFindByOrderID`, `btnCancelOrder`, 및 `btnFillOrder` Click 이벤트 처리기.|  
  
## <a name="BKMK_testyourapplication"></a> 응용 프로그램 테스트  
 빌드 및 각 Click 이벤트 처리기를 코딩 한 후 응용 프로그램을 테스트 하려면 F5 키를 선택 하 고 코딩을 마친 후 다음입니다.
