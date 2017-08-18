var MikroNode = require('mikronode');
// Create API instance to a host.
var device = new MikroNode('192.168.50.1');
// device.setDebug(MikroNode.DEBUG);

// Connect to MikroTik device
device.connect('admin','12345').then(
  function(conn) { 
    // When all channels are marked done, close the connection.
    conn.closeOnDone(true);

    var hsChannel=conn.openChannel();
    // Adding hotspot user
    hsChannel.write(['/ip/hotspot/user/add','=limit-uptime=1h', '=name=anggwapo', '=password=nimckoy', '=server=hotspot1'])
      .then(result=>{ 
        // return when success.
        console.log('Successfully added hotspot user.');
      })
      .catch(error=>{
        // return if error.
        var data=MikroNode.resultsToObj(error);
        console.log('Error adding Hotspot User.');
      });
  }
);