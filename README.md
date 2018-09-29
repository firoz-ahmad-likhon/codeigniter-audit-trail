# User Audit Trail #

It is an attempt to add user audit trail with CodeIgniter framework. I think it is a very convenient way to track user activities in the database.

### Installation ###

* Put all files into your projects directory respectively.
* Check config.php for <code>$config['subclass_prefix']</code> this value. If it is not <code>'MY_'</code> then rename <code>MY_DB_mysqli_driver.php</code> and <code>MY_Loader.php</code> to your value.
* To enable listening change set <code>$config['audit_enable'] = TRUE</code> in config/the trail.php
* You can start/stop to record insert, update, delete. please read carefully the trail.php

Now you are ready to browse the application.

### Database Table ###
* Run the sql in your database.


        CREATE TABLE `user_audit_trails` (
          `id` int(11) NOT NULL,
          `user_id` int(11) NOT NULL,
          `event` enum('insert','update','delete') NOT NULL,
          `table_name` varchar(128) NOT NULL,
          `old_values` text,
          `new_values` text NOT NULL,
          `url` varchar(255) NOT NULL,
          `name` varchar(128) NOT NULL,
          `ip_address` varchar(45) NOT NULL,
          `user_agent` varchar(255) NOT NULL,
          `created_at` timestamp NULL DEFAULT NULL
        ) ENGINE=InnoDB DEFAULT CHARSET=utf8;
    
 
        ALTER TABLE `user_audit_trails`
          ADD PRIMARY KEY (`id`);
    
        ALTER TABLE `user_audit_trails`
          MODIFY `id` int(11) NOT NULL AUTO_INCREMENT;
        COMMIT;
    
### Further Work ###

Now it is your turn to make model and view for presenting the audit data. Happy coding..
