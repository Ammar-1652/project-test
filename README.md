# project-test
this is test repo
first repo after the course
<h1>Hello, world</h1>
https://www.guru99.com/asp-net-session-management.html
https://github.com/YousefElbilkasy/College_Management_System_Using_Asp
https://drive.google.com/file/d/1PSXeqzL10Tf-_l5SR_ugaZKjI45lWPuw/view?usp=drive_link
=========================================
protected void confirmDeleteBtn_Click(object sender, EventArgs e)
        {
            Button button = (Button)sender;
            int studentId = Convert.ToInt32(button.CommandArgument);

            string connectionString = ConfigurationManager.ConnectionStrings["ConnectionString"].ConnectionString;

            using (SqlConnection connection = new SqlConnection(connectionString))
            {
                connection.Open();

                // Delete related records in StudentAttendance table
                string deleteAttendanceQuery = "DELETE FROM StudentAttendance WHERE StudentID = @StudentID";
                using (SqlCommand attendanceCommand = new SqlCommand(deleteAttendanceQuery, connection))
                {
                    attendanceCommand.Parameters.AddWithValue("@StudentID", studentId);
                    attendanceCommand.ExecuteNonQuery();
                }
                // Delete related records in StudentCoursese table
                string deleteStudentCourseseQuery = "DELETE FROM StudentsCourses WHERE StudentID = @StudentID";
                using (SqlCommand courseCommand = new SqlCommand(deleteStudentCourseseQuery, connection))
                {
                    courseCommand.Parameters.AddWithValue("@StudentID", studentId);
                    courseCommand.ExecuteNonQuery();
                }

                // Delete the student
                string deleteQuery = "DELETE FROM Students WHERE StudentID = @StudentID";
                using (SqlCommand command = new SqlCommand(deleteQuery, connection))
                {
                    command.Parameters.AddWithValue("@StudentID", studentId);
                    command.ExecuteNonQuery();
                    Response.Redirect(Request.Url.ToString());
                    //    int rowsAffected = 

                    //    if (rowsAffected > 0)
                    //    {
                    //        ShowMessage("Success");
                    //        Response.Redirect(Request.Url.ToString());
                    //    }
                    //    else
                    //    {
                    //        ShowError("Failed");
                    //    }
                    //}

                    void ShowMessage(string txt)
                    {
                        // Display success message to the user
                        ClientScript.RegisterStartupScript(this.GetType(), "alert", "alert('" + txt + "');", true);
                    }

                    void ShowError(string txt)
                    {
                        // Display error message to the user
                        ClientScript.RegisterStartupScript(this.GetType(), "alert", "alert('" + txt + "');", true);
                    }
                }
            }



        }
