設定vsftpd使用系統user登入，預設路徑/home/$USER/ftp

apt-get install vsftpd
vi /etc/vsftpd.conf

  anonymous_enable=NO
  local_enable=YES
  write_enable=YES


  chroot_local_user=YES
  allow_writeable_chroot=YES
  user_sub_token=$USER
  local_root=/home/$USER/ftp

  userlist_enable=YES
  userlist_file=/etc/vsftpd.userlist
  userlist_deny=NO


  pam_service_name=ftp



echo "ftpuser" | sudo tee -a /etc/vsftpd.userlist


service vsftpd restart
