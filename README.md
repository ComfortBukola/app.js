var http = require("http");
var fs = require("fs");
fs.writeFile("message.txt", "Submit Form", function(err) {
  if (err) throw err;
  console.log("Form submitted successfully.");
});

http
  .createServer(function(req, res) {
    res.writeHead(200, { "Content-Type": "text/html" });
    res.write("Please enter a message below:");
    res.write('<form action="/message" method="POST">');
    res.write('<label for="msg">Message:</label>');
    res.write('<input type="text" id="message" name="message"></br>');
    res.write('<input type="submit" value="Submit">');
    res.write("</form>");
    return res.end();
  })
  .listen(8080);
