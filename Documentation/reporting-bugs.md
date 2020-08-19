---
jetcd-core 0.5.0, my watch can't receieve nodes's change
---
First, it's my watch code:
Client client = Client.builder().endpoints(endpoints.split(",")).user(ByteSequence.from(user, DEFAULT_CHARSET))
				.password(ByteSequence.from(password, DEFAULT_CHARSET)).build();
		Watch watchClient = client.getWatchClient();

		Watch.Listener listener = Watch.listener(response -> {
			for (WatchEvent event : response.getEvents()) {
				System.out.println(System.currentTimeMillis() + ":" + "update---key=" + key + ",content=" + content);
			}
		});
		watchClient.watch(ByteSequence.from("/xxx", DEFAULT_CHARSET), WatchOption.newBuilder()
				.withPrefix(ByteSequence.from("/xxx", DEFAULT_CHARSET)).build(), listener);
    synchronized (xxxx.class) {
			while (true) {
				xxxx.class.wait();
			}
		}

Second，the network of the computer which the watchClient in was down about 2 minutes.

After 2 minutes, the network was ok. Then, the node was changed. But i can't receieve the change.  
I have to restart my service if i want to receieve changes.
Also, i fond that, there has 4 threads like 'grpc-default-worker-ELG-x-x', but there has 2 in normal.

