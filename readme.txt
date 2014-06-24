Git is a  vresion control system
git is free 
<<<<<<< HEAD
hello world

 //<summary>
        //验证用户名密码是否正确
        //</summary>
        //<param name="nUserID">用户ID</param>
        //<param name="nPassWord">加密后的密码</param>
        //<param name="nMsg">返回的错误信息</param>
        //<returns>用户名密码是否正确</returns>
        private bool IsValid(string UserName, string md5Password, string DBName, string Server, out string nMsg)
        {
            nMsg = "";
            ConnectionClass.DBName = DBName;
            ConnectionClass.ServerName = Server;
            ConnectionClass.UserName = "sa";
            ConnectionClass.Password = "~kph@13922165736";
            ConnectionClass.ConnectionString = ConnectionClass.SQLStr;
            ConnectionClass.DBType = "MSSQL";

            try
            {
                string strSQL = "select e.EmployeeID As UserID, e.LoginName, e.DisplayName As UserName  "
                + "From (tbe_EmployeeMst as e Left Join tbe_LocationMst as l On e.Location = l.Code) "
                + "where LoginName = @UserName "
                + "and [Password] = @Password and e.Flag <> 'D' and AccountStatus <> '3' and WebSiteLogin = 'Y' ";
                SQL sql = new SQL(strSQL, ConnectionClass.ConnectionString);
                sql.Parameters.AddWithValue("@UserName", UserName);
                sql.Parameters.AddWithValue("@Password", md5Password);
                DataTable dt = sql.ExecuteDataSet("Login").Tables[0];
                if (dt.Rows.Count == 1)                
                {
                    return true;
                }
                else
                {
                    nMsg = "对不起，你无权调用此Web服务。";
                    return false;
                }
            }
            catch
            {
                nMsg = "对不起，你无权调用此Web服务。";
                return false;
            }
        }
=======

>>>>>>> 9b3c8b6f02bd56f9e9331273f8cd1deb276c688c
