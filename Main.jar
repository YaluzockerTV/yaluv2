package de.yalu.main;

import java.io.BufferedReader;
import java.io.InputStreamReader;

import javax.security.auth.login.LoginException;

import de.yalu.main.listener.CommandListener;
import net.dv8tion.jda.api.OnlineStatus;
import net.dv8tion.jda.api.entities.Activity;
import net.dv8tion.jda.api.sharding.DefaultShardManagerBuilder;
import net.dv8tion.jda.api.sharding.ShardManager;

public class Main {
	
	public ShardManager Shardman;

	public static void main(String[] args)  {
		
			try {
				new Main();
			} catch (LoginException e) {
			}
		
	}
	
	public Main() throws LoginException, IllegalArgumentException {
		DefaultShardManagerBuilder builder = new DefaultShardManagerBuilder();
		builder.setToken("NjA0NzAzMDU2Mjg1Nzk0MzEz.XTxzoQ.ewOa8Q4wlcS77S2jXZznJG0uv9Y");
		
		builder.setActivity(Activity.watching("you"));
		builder.setStatus(OnlineStatus.ONLINE);
		
		builder.addEventListeners(new CommandListener());
		
		Shardman = builder.build();
		System.out.println("Bot online!");
		
		shutdown();
	}
	
	public void shutdown( ) {
		
		new Thread(() -> {
			
			String line = "";
			BufferedReader reader = new BufferedReader(new InputStreamReader(System.in));
				try {
					while((line = reader.readLine()) != null) {
						if(line.equalsIgnoreCase("exit")) {
							if(Shardman != null) {
								Shardman.setStatus(OnlineStatus.OFFLINE);
								Shardman.shutdown();
								System.out.println("Bot offline");
							}
							else {
								System.out.println("Use exit to shutdown");
							}
						}
					}
				} catch (Exception e) {
					e.printStackTrace();
				}
		}).start();
	}
	
}
