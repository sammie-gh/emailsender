# emailsender
java class email sender


add the two java classs to your app 

also add to gradle

   implementation files('libs/activation.jar')
    implementation files('libs/additional.jar')
    implementation files('libs/mail.jar')

 next to use the below code 
final ProgressDialog dialog = new ProgressDialog(BookingActivity.this);
        dialog.setTitle("Sending ");
        dialog.setMessage("Please wait");
        dialog.show();
        Thread sender = new Thread(new Runnable() {
            @Override
            public void run() {
                try {
                    GMailSender sender = new GMailSender("youremailaddress", "yourpassword");
                    sender.sendMail(
                            emailSubject,
                            emailBody,
                            "evansdrah@gmail.com",
                            itemMails);
                    dialog.dismiss();
                } catch (Exception e) {
                    Log.e("mylog", "Error: " + e.getMessage());
                }
            }
        });
        sender.start();
