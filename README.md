# Github-Tutorial
<Page
    x:Class="Loginpage.MainPage"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:local="using:Loginpage"
    xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
    xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
    mc:Ignorable="d">

    <Grid Background="LightBlue"  Height="400" >
        <TextBlock x:Name="Name"  Text="Name:" Margin="290,50,0,0"  HorizontalAlignment="Left" VerticalAlignment="Top"/>
        <TextBox HorizontalAlignment="Center" Margin="0,50,0,0" VerticalAlignment="Top" PlaceholderText="Name is required" TextWrapping="NoWrap"/>
        <TextBlock x:Name="PAN"  Text="Pan:"   Margin="290,90,0,0" HorizontalAlignment="Left" VerticalAlignment="Top"/>
        <TextBox HorizontalAlignment="Center"  Margin="0,90,0,0" VerticalAlignment="Top"  PlaceholderText="Pan is required" TextWrapping="NoWrap"/>
        <TextBlock x:Name="AADHAR"  Text="Adhar:" Margin="290,120,0,0"  HorizontalAlignment="Left" VerticalAlignment="Top"/>
        <TextBox HorizontalAlignment="Center" Margin="0,130,0,0" VerticalAlignment="Top" PlaceholderText="Aadhar is required" TextWrapping="NoWrap"/>
        <Button x:Name="login" Content="login"  Margin="0,180,0,0"   Background="CadetBlue"  Click="login_Click" HorizontalAlignment="Center" VerticalAlignment="Top"/>
    </Grid>
</Page>

        private async void login_Click(object sender, RoutedEventArgs e)
        {
            if(Name.Text==null)
            {
                MessageDialog msg1 = new MessageDialog(" Name value required");
                await msg1.ShowAsync();
            }
            else
            {
                MessageDialog msg1 = new MessageDialog("Login  Successful");
                await msg1.ShowAsync();
            }

            if(AADHAR.Text.Length==12)
            {
                MessageDialog msg1 = new MessageDialog("AADHAR  verified");
                await msg1.ShowAsync();
            }
            else
            {
                MessageDialog msg1 = new MessageDialog(" invalid aadhar");
                await msg1.ShowAsync();
            }
            char []ch =PAN.Text.ToCharArray() ;

            if (PAN.Text.Length != 10)
            {
                MessageDialog msg1 = new MessageDialog(" enter valid PAN");
                await msg1.ShowAsync();
            }
            for (int i = 0; i < 10; i++)
            {
                if ((i >= 0 && i <= 4) && ( ch[i] < 'A' || ch[i] > 'Z'))
                {
                    MessageDialog msg1 = new MessageDialog(" invalid PAN");
                    await msg1.ShowAsync();
                }
                else if ((i > 4 && i <= 8) && (ch[i] < 48 || ch[i] > 57))
                {
                    MessageDialog msg1 = new MessageDialog(" invalid PAN");
                    await msg1.ShowAsync();
                }
                else if (i == 9 && (ch[i] < 'A' || ch[i] > 'Z'))
                {
                    MessageDialog msg1 = new MessageDialog(" invalid PAN");
                    await msg1.ShowAsync();
                }
            }
            MessageDialog msg = new MessageDialog("Login  Successful");
            await msg.ShowAsync();
        }
